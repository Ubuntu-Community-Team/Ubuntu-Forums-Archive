---
title: "Samba, Avahi, and the 10.5 Leopard Finder (SOLVED!)"
date: 2009-04-18
forum: Server Platforms
---

### Post by ajslater on 2009-04-18
This is a response to this archived thread: [Samba, Avahi, and the 10.5 Leopard Finder](http://ubuntuforums.org/showthread.php?t=612442)

Actual mac servers combine all the services into one service group with the same name. This lets the leopard finder combine like services into one icon. This is most apparent when you have afp, samba (avahi), and samba broadcasting its NetBIOS name. If you make them all one service group with the same name (same as the NetBIOS name ‘%h’) The Leopard finder will show only one icon and preferentially use afp over samba over finding samba via NetBIOS.

This solution makes it so you don't have to turn off DBUS in avahi. If you want to run afp and samba and also want access to the samba shares from your mac, then you would want to move the samba service into its own uniquely named service group, like "%h (Windows)" or something.
But, for leopard to hide the service it discovers via NetBIOS, it needs a zeroconf service with the same name to stack on top of it, either afp or samba.

Also, this guy taught me how to [specify your finder icon for a service group](http://www.simonwheatley.co.uk/2008/04/06/avahi-finder-icons/).

Example:
[B]/etc/avahi/services/all.service
[/B]
```

<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
    <name replace-wildcards="yes">%h</name>
    <service>
        <type>_afpovertcp._tcp</type>
        <port>548</port>
    </service>
    <service>
        <type>_smb._tcp</type>
        <port>139</port>
    </service>
    <service>
        <type>_ssh._tcp</type>
        <port>22</port>
    </service>
    <service>
        <type>_sftp-ssh._tcp</type>
        <port>22</port>
    </service>
    <service>
        <type>_device-info._tcp</type>
        <port>0</port>
        <txt-record>model=RackMack</txt-record>
    </service>
</service-group>

```

---

### Post by ergosteur on 2011-11-28
I'd just like to add that Lion breaks this. I found the solution on Apple discussions:

[https://discussions.apple.com/thread/3196311?start=30&tstart=0](https://discussions.apple.com/thread/3196311?start=30&tstart=0)

> Solution found for the avahi problem!

 

Just change the port in the samba.service from 139 to 445, see below

 

<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

 

<service-group>

    <name replace-wildcards="yes">%h</name>

    <service>

        <type>_smb._tcp</type>

        <port>445</port>

    </service>

    <service>

         <type>_device-info._tcp</type>

         <port>0</port>

         <txt-record>model=Xserve</txt-record>

    </service>

</service-group>

 

I've searched over days before i've found the solution FU APPLE!

Just tell us and everything is ok, but changing without documentationi is NOT ok.

---

