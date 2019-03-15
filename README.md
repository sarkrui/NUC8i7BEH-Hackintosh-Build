# [GUIDE] Building a Mac mini beast with NUC8i7BEH
### Overview

This guide derives from @Rehabman's [[Guide] Booting the OS X installer on LAPTOPS](https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/) and [[Guide] Intel NUC7NUC8 using Clover UEFI (NUC7i7Bxx,NUC8i7Bxx,etc)](https://www.tonymacx86.com/threads/guide-intel-nuc7-nuc8-using-clover-uefi-nuc7i7bxx-nuc8i7bxx-etc.261711/) but the procedure has been simplied in order to provide a quick guide to install Mojave on the NUC8i7BEH. 

### Performance

![image-20190313124555196](https://i.imgur.com/UJxsDaw.png)

![image-20190313124640383](https://i.imgur.com/0VkvCy7.png)



#### Specs

* **HyperX Impact** DDR4 SODIMM 16GB * 1 (Recommend two sticks in dual-channel, 16GB of RAM works fine so far for me)  *Crucial DDR4 SODIMM 16GB* I bought was **not compatible** with my NUC8. For more information about the recommended RAMs by Intel, see [Memory Modules](http://compatibleproducts.intel.com/ProductDetails/ExportPeripheralInfo?moduleName=Intel%C2%AE%20NUC&productType=Kits&productName=Intel%C2%AE%20NUC%20Kit%20NUC8i7BEH) 
* **Crucial MX500** 1000G SATAIII SSD (I need the M.2 slot for Wi-FI/Bluetooth.)
* **BCM943602CDP** Wi-Fi/Bluetooth + [M.2 NGFF Key B+M Adapter](https://www.ebay.co.uk/itm/Wireless-Card-Module-to-M-2-NGFF-Key-B-M-Adapter-BCM94360CD-for-Mac-OS-12-6-Pin/264001220361?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649) 
* **Mojave 10.14.2** Final Cut Pro has better performance on 10.14.2, less exporting time and better stability than the performance on 10.14.3.



#### Works

* **AirDrop, Handoff** (Apple Wi-Fi/Bluetooth required)
* **iMessage** (complete serial required) 
* **All USB3.1 Gen1/USB2.0 ports**
* **USB3.1 Type-c Hotplug**
* **Hardware Acceleration supported.** (Final Cut Pro X, VideoProc, Compressor tested.)



#### *Not Validated Yet*

* Thunderbolt 3 eGPU *(WIP)*



### Preparation 

#### BIOS settings

* BIOS version **0056** (<u>Please do not use the latest one, 0064</u>. If so, please downgrade to 0056, I have attached the firmware in the respository since it was no longer provided from Intel support.) 

BIOS setup can be accessed by mashing the **F2** key while booting up. It will get you to the main BIOS setup screens. To start, choose "**Load Defaults**"  (choose from the menu or press **F9** in the BIOS setup).

Then change:

- Boot -> Boot Configuration, disable "**Network Boot**"
- Power -> Secondary Power Settings, "**Wake on LAN from S4/S5**", set to "**Stay Off**"
- Boot -> Secure Boot, disable "**Secure Boot**" 
- Devices -> OnBoard Devices, disable "**Bluetooth**" 

Suggested:

- Boot -> Boot Priority -> Legacy Boot Priority, enable "**Legacy Boot**".



### Installation

#### Solution 1 (WIP) Recommended

* [Mojabe 10.14.2 Download](https://blog.daliansky.net/macOS-Mojave-10.14.2-18C54-official-version-with-Clover-4792-original-image.html)
* [Install macOS with etcher](https://blog.daliansky.net/MacOS-installation-tutorial-XiaoMi-Pro-installation-process-records.html)

#### Solution 2 (WIP)

* [[Guide] Installing macOS Mojave (10.14.2) on Intel NUCi5BEH using Clover UEFI](https://www.tonymacx86.com/threads/guide-installing-macos-mojave-10-14-2-on-intel-nuci5beh-using-clover-uefi.268502/)

### Post-installation

#### Clover EFI 

Download the latest EFI Clover (see [release](https://github.com/sarkrui))

#### Wi-Fi/Bluetooth Adapter

![Untitled-1](https://i.imgur.com/YxZvkLv.jpg)

- 2-pin JST 1.00mm (pitch) connected to the adapter 
- 4-pin JST 1.25mm (pitch) connected to the NUC internal USB2.0 connector (see "G" "H")

##### Scheme 

![BT_InternalUSBHeader_Scheme](https://i.imgur.com/nqRlweB.png)

#### FRC Reverse Proxy

Frp is a fast reverse proxy to help you expose a local server behind a NAT or firewall to the internet. As of now, it supports tcp & udp, as well as http and https protocols, where requests can be forwarded to internal services by domain name. For example, with Frp, VNC port (5900), SSH port (22), and FTP port (445) on Macs behind a NAT, can be exposed to the public. Therefore, a user can have access to **Screen Sharing**, **File Sharing** remotely.

### Credit

This project is highly 

* [@RehabMan](https://www.tonymacx86.com/members/rehabman.429483/)

* [@Daliansky](https://blog.daliansky.net)
* [@GoingDark](https://www.tonymacx86.com/members/2192833/)