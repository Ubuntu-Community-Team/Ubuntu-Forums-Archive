---
title: "VirtualBox Error Guest Don't Start VERR_CFGM_VALUE_NOT_FOUND ( SOLVED )"
date: 2010-03-21
forum: Virtualisation
---

### Post by jmazaredo on 2010-03-21
**THIS PROBLEM IS SOLVED ( I post here so that if some new user of virtual box stumble on the problem )**


[img]http://i43.tinypic.com/2yx42ug.png[/img]

I got this problem when I'm trying to configure forwarding port 

```

VBoxManage setextradata WindowsXp "VBoxInternal/Devices/pcnet/0/LUN#0/Config/www/HostPort" 80
VBoxManage setextradata WindowsXp "VBoxInternal/Devices/pcnet/0/LUN#0/Config/www/GuestPort" 80
VBoxManage setextradata WindowsXp "VBoxInternal/Devices/pcnet/0/LUN#0/Config/www/Protocol" TCP
```

After struggling for forward to work changed the network card from pcnet to intel pro .

on the process of starting the virtualbox this error showed. Tried to change the card back to pcnet but no avail.

==============================================================================================
[center][color=#FF0000]
**Fixed the error**[/color][/center]

[email]jmazaredo@linux:~/.Virtua[/email]lBox/Machines/WindowsXp$ gedit WindowsXp.xml 

removed what seems to be get stacked up 
    ```
<ExtraDataItem name="VBoxInternal/Devices/e1000/0/LUN#0/Config/www/GuestPort" value="80"/>
      <ExtraDataItem name="VBoxInternal/Devices/e1000/0/LUN#0/Config/www/HostPort" value="80"/>
      <ExtraDataItem name="VBoxInternal/Devices/e1000/0/LUN#0/Config/www/Protocol" value="TCP"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort" value="22"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort" value="22"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol" value="TCP"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/www/GuestPort" value="80"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/www/HostPort" value="80"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/www/Protocol" value="TCP"/>

```

```
<Adapter slot="0" enabled="true" MACAddress="080027666DC5" cable="true" speed="0" type="Am79C970A"/>
        <Adapter slot="1" enabled="false" MACAddress="080027368A27" cable="true" speed="0" type="82540EM">
          <BridgedInterface name="wlan0"/>
        </Adapter>
        <Adapter slot="2" enabled="false" MACAddress="080027CEB988" cable="true" speed="0" type="Am79C973">
          <InternalNetwork name="intnet"/>
        </Adapter>
        <Adapter slot="3" enabled="false" MACAddress="080027CDDF91" cable="true" speed="0" type="virtio">
          <InternalNetwork name="intnet"/>
        </Adapter>
        <Adapter slot="4" enabled="false" MACAddress="0800273E9836" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="5" enabled="false" MACAddress="080027D69F71" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="6" enabled="false" MACAddress="080027D98786" cable="true" speed="0" type="Am79C973"/>
        <Adapter slot="7" enabled="false" MACAddress="080027FEB146" cable="true" speed="0" type="Am79C973"/>
```
[b]
VirtualBox should not be working when editing.[/b]

---

