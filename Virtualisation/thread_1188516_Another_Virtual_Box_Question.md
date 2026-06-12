---
title: "Another Virtual Box Question"
date: 2009-06-15
forum: Virtualisation
---

### Post by hufferd on 2009-06-15
I seem to be some what confused I am running Windows 7 with in virtual box and I can't seem to SHARE or access the folders I would like to on the host machine ie. documents,Music,videos & a few others I have them set up as shared with in virtual box but passed that I am stuck :( 

Any ideas?

---

### Post by hufferd on 2009-06-16
:confused: 

+1

---

### Post by Jose Catre-Vandis on 2009-06-17
Have you installed Additions?

Just read your other post and you have installed additions!

Have you looked under Network Places the shares should be there somewhere (not running W7 so don't know what MS called it)

---

### Post by nfox on 2009-06-17
[http://www.virtualbox.org/changeset/15967]("http://www.virtualbox.org/changeset/15967")
You are aware that this is a major issue yet to be resolved by the Sun team? This doesn't affect VMWare or QEMU as far as I'm aware. I dabbled with 7 but the shared folder can in fact work just not out of the (virtual) box.

Fear not...

In Windows 7:
1) Open regedit
2) Navigate to
HKLM\SYSTEM\Select>Current
3) The value "Current" for me had the data "1". That value tells which control set is in use. So I navigated to
HKLM\SYSTEM\ControlSet001\Services\VBoxGuest>Start
4) I changed the data of Start to "0" (no quotes) meaning "start at boot time"
5) On my system no "LoadOrderGroup" was specified for VBoxGuest. I added a new "LoadOrderGroup" (no quotes) string value and set its data to "Base" (again no quotes).
6) Reboot. When the system comes up Shared Folders should be working.

---

### Post by H2SO_four on 2009-06-17
I just changed one of my folders in my /home directory to full sharing permissions within the network.  Then while in my Win7 VB I located the shared folder through the network places.  This way I have full read/write acess and don't have to fuss with it much to make it work.

---

### Post by hufferd on 2009-06-21
> **nfox said:**
> [http://www.virtualbox.org/changeset/15967]("http://www.virtualbox.org/changeset/15967")
You are aware that this is a major issue yet to be resolved by the Sun team? This doesn't affect VMWare or QEMU as far as I'm aware. I dabbled with 7 but the shared folder can in fact work just not out of the (virtual) box.

Fear not...

In Windows 7:
1) Open regedit
2) Navigate to
HKLM\SYSTEM\Select>Current
3) The value "Current" for me had the data "1". That value tells which control set is in use. So I navigated to
HKLM\SYSTEM\ControlSet001\Services\VBoxGuest>Start
4) I changed the data of Start to "0" (no quotes) meaning "start at boot time"
5) On my system no "LoadOrderGroup" was specified for VBoxGuest. I added a new "LoadOrderGroup" (no quotes) string value and set its data to "Base" (again no quotes).
6) Reboot. When the system comes up Shared Folders should be working.


I still am not getting the share to work :( I went through these steps and everything seemed to be set as you have it here. :( I guess no share for me :(

---

### Post by hilltop on 2009-06-21
As a temporary work-around, do you have an external Windows machine on your LAN on which you can set up a share that both your Host and your Guest can see?  If so, make sure you set the networking type of your Guest OS to Bridged.  Vbox defaults to NAT which works fine when the Guest simply needs to send requests and receive responses from the internet, such as web browsing.  But a NAT firewall (implemented virtually in Vbox) will not pass the non-TCP/IP Windows NetBIOS packets, resulting in the Guest OS not having visibility into Windows shares on your LAN.  When you change the Guest's networking type to Bridged, the Guest looks to your LAN like just another host and requests a DHCP address from your DHCP server, presumably your router.  Then, all Windows network share traffic can pass to/from your Guest and it should see all Windows shares on the LAN.  Not sure if the Vbox networking type (there are 4 types in the latest version of Vbox) affects internal shares between the Host and the Guest, which is what it sounds like you are trying to do.

---

