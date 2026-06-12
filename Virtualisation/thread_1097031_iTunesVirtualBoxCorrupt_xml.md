---
title: "iTunes/VirtualBox/Corrupt xml"
date: 2009-03-15
forum: Virtualisation
---

### Post by Paperfairy on 2009-03-15
Last night, I installed VBox in order to get support for my iPod Touch. However, I recently learned the hard way that iTunes kidnapped all my music from my Windows partition, and I have no idea as to w.here it placed it... and now I can't start VirtualBox to get it back, because....


> Could not load the settings file '/home/username/.VirtualBox/Machines/XP/XP.xml'.
Premature end of data in tag VirtualBox line 3.
Location: '/home/username/.VirtualBox/Machines/XP/XP.xml', line 71 (3), column 38.


Result Code: 
VBOX_E_XML_ERROR (0x80BB000A)
Component: 
VirtualBox
Interface: 
IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}

The file is as follows:

> 
<?xml version="1.0" encoding="UTF-8"?>
<!-- Sun xVM VirtualBox Machine Configuration -->
<VirtualBox xmlns="http://www.innotek.de/VirtualBox-settings" version="1.6-linux">
  <Machine uuid="{62272c0f-bf88-4ca0-a69f-338248e388d9}" name="XP" OSType="WindowsXP" lastStateChange="2009-03-15T17:12:15Z">
    <ExtraData>
      <ExtraDataItem name="GUI/LastWindowPostion" value="4,47,800,646"/>
      <ExtraDataItem name="GUI/Fullscreen" value="off"/>
      <ExtraDataItem name="GUI/Seamless" value="off"/>
      <ExtraDataItem name="GUI/AutoresizeGuest" value="on"/>
      <ExtraDataItem name="GUI/SaveMountedAtRuntime" value="yes"/>
    </ExtraData>
    <Hardware>
      <CPU count="1">
        <HardwareVirtEx enabled="false"/>
      </CPU>
      <Memory RAMSize="200"/>
      <Boot>
        <Order position="1" device="Floppy"/>
        <Order position="2" device="DVD"/>
        <Order position="3" device="HardDisk"/>
      </Boot>
      <Display VRAMSize="12" monitorCount="1" accelerate3D="false"/>
      <RemoteDisplay enabled="false" port="3389" authType="Null"/>
      <BIOS>
        <ACPI enabled="true"/>
        <IOAPIC enabled="false"/>
        <Logo fadeIn="true" fadeOut="true" displayTime="0"/>
        <BootMenu mode="MessageAndMenu"/>
        <TimeOffset value="0"/>
        <PXEDebug enabled="false"/>
        <IDEController type="PIIX4"/>
      </BIOS>
      <DVDDrive passthrough="false">
        <Image uuid="{16ecfa0a-544d-4c23-a904-e9ab33031d77}"/>
      </DVDDrive>
      <FloppyDrive enabled="true"/>
      <USBController enabled="true" enabledEhci="true"/>
      <SATAController enabled="false" PortCount="1" IDE0MasterEmulationPort="0" IDE0SlaveEmulationPort="1" IDE1MasterEmulationPort="2" IDE1SlaveEmulationPort="3"/>
      <Network>
        <Adapter slot="0" enabled="true" MACAddress="080027D041D7" cable="true" speed="0" type="Am79C973">
          <NAT/>
        </Adapter>
        <Adapter slot="1" enabled="false" MACAddress="0800270E8748" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="2" enabled="false" MACAddress="080027EA028E" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="3" enabled="false" MACAddress="08002766AFB5" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="4" enabled="false" MACAddress="080027CE12A4" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="5" enabled="false" MACAddress="080027006669" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="6" enabled="false" MACAddress="080027572E92" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="7" enabled="false" MACAddress="0800277CA24F" cable="true" speed="0" type="Am79C973"/>
      </Network>
      <UART>
        <Port slot="0" enabled="false" IOBase="0x3f8" IRQ="4" hostMode="Disconnected"/>
        <Port slot="1" enabled="false" IOBase="0x3f8" IRQ="4" hostMode="Disconnected"/>
      </UART>
      <LPT>
        <Port slot="0" enabled="false" IOBase="0x378" IRQ="4"/>
        <Port slot="1" enabled="false" IOBase="0x378" IRQ="4"/>
      </LPT>
      <AudioAdapter controller="AC97" driver="Null" enabled="false"/>
      <SharedFolders>
        <SharedFolder name="OS" hostPath="/media/OS" writable="true"/>
      </SharedFolders>
      <Clipboard mode="Bidirectional"/>
      <Guest memoryBalloonSize="0" statisticsUpdateInterval="0"/>
      <GuestProperties>
        <GuestProperty name="/VirtualBox/HostInfo/GUI/LanguageID" value="C" timestamp="1237098988685449000" flags=""/>
        <GuestProperty name="/VirtualBox/GuestInfo/OS/Product" value="Windows XP Professional" timestamp="1237101096826147000" flags=""/>
        <GuestProperty name="/VirtualBox/GuestInfo/OS/Release" value="5.1.2600" timestamp="1237101096826974000" flags=""/>
        <GuestProperty name="/VirtualBox/GuestInfo/OS/ServicePack" value="2" timestamp="1237101096827564000" flags=""/>
        <GuestProperty name="/VirtualBox/GuestAdd/InstallDir" value="C:/Program Files/Sun/xVM VirtualBox Guest Additions" timestamp="1237101096828857000" flags=""/>
        <GuestProperty name="/VirtualBox/GuestAdd/Revision" value="42893" time



What should I do to fix it?

---

