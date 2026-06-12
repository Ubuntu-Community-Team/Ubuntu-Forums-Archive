---
title: "[IDEA] Propper avahi/mDNS use!!!"
date: 2007-12-16
forum: Ubuntu Brainstorm
---

### Post by puccaso on 2007-12-16
i have noticed that ubuntu and most the linux flavours do not use AVAHI propperly..

we have an abundence of things we could do with it, but it hasnt been done once since avahi's release. yes ok we have a service applet and yes ok - we have gnome-user-share but what why not the following.

when programs are installed, that are network apps, dpkg should ask us if we want to advertise the service via avahi.. 

this can be done currently by the following :
create the folliwing files

/etc/avahi/service/samba.service
```
 <?xml version="1.0" standalone='no'?>
<service-group>
  <name>Server SMB</name>
  <service>
    <type>_smb._tcp</type>
    <port>139</port>
  </service>
</service-group>  
```**NOTE: vino already does this, yay! but as an example do it anyway to test...**

/etc/avahi/service/ rfb.service
```
 <?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
  <name>Server Desktop</name>
  <service>
    <type>_rfb._tcp</type>
    <port>5900</port>
  </service>
</service-group>
```when you do this - you will see, in the menu, under internet - two options that are poped up magically to search for smb shares and rfb shares..

**NOTE: this doesnt happen when vino advertises the service.**




i want to see all of the following items advertised no my network via avahi.[LIST]
[*]**skype,**
[*]**ekiga **<~happens already, yay!
[*]**warsow server**
[*]**quake**
[*]**games**!!!! <~IMAGING LOCALLY NETWORKED GAMES
[*]**glipper** <~imagine just sharing info over a network by copying it... (with authentication obviously)
[*]**f-spot gallery**
[*]**vlc **<~has some sort of bonjour advertising but its naff and should be improved.
[*]**azurues** <~on windows, it acts as a upnp server for windowsmobile11 to play directly from the software, well why cant we get some sort of similar advertising working with avahi[/LIST]common ubuntu!!


** note: original avahi service files from [mcewen98]("http://ubuntuforums.org/member.php?u=26163")**

---

