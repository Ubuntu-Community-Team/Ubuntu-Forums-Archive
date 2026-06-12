---
title: "SAMBA 4 problem"
date: 2010-05-03
forum: Server Platforms
---

### Post by Vegan on 2010-05-03
I installed SAMBA 4 and its having problems with my smb.conf so has anybody seens any issues?

---

### Post by CharlesA on 2010-05-03
Haven't had any problems with it in Lucid or Karmic.

What does running ```
testparm
``` say?

---

### Post by Vegan on 2010-05-04
I removed it and want back to the old version with 10.04

---

### Post by CharlesA on 2010-05-04
Which version is the old version?

I just checked and it looks like I am running Samba 3.4.7 on 10.04.

That was the one that was installed when I did an apt-get:

```
apt-get install samba
```

How did you install Samba 4?

---

### Post by neutron68 on 2010-05-05
SAMBA is working for you in 10.04???

I'm running Mythbuntu (the Mythtv/Ubuntu distro).
Mythbuntu uses the XFCE desktop rather than Gnome.
([http://www.mythbuntu.org/](http://www.mythbuntu.org/))

Last night, I used the Update Manager and did the online upgrade from 9.10 to 10.04, it seemed to go ok.  When I started exploring the new system, I found my SAMBA shared folders which were 100% accessable from other PCs in my home network under 9.10, are not accessable from other PCs under 10.04, AND there are no controls for configuring shared folders any more!

Bottom line:  SAMBA is broken in my 10.04 system.  Any idea how to fix it?

Help appreciated,
Eric

---

### Post by krodrigue on 2010-05-05
Go to Applications, Ubuntu Software Center, then in the search box at the top right add samba and you will see...Samba...create, modify, and delete samba shares. That's what you are looking for to add and remove shares.

---

### Post by beregu on 2010-05-05
> **neutron68 said:**
> SAMBA is working for you in 10.04???

I'm running Mythbuntu (the Mythtv/Ubuntu distro).
Mythbuntu uses the XFCE desktop rather than Gnome.
([http://www.mythbuntu.org/](http://www.mythbuntu.org/))

Last night, I used the Update Manager and did the online upgrade from 9.10 to 10.04, it seemed to go ok.  When I started exploring the new system, I found my SAMBA shared folders which were 100% accessable from other PCs in my home network under 9.10, are not accessable from other PCs under 10.04, AND there are no controls for configuring shared folders any more!

Bottom line:  SAMBA is broken in my 10.04 system.  Any idea how to fix it?

Help appreciated,
Eric

I clean installed Ubuntu 10.04 instead online upgrade. First, I thought clean installation would take much less time than online upgrade, but it wasn't setup was always freezing.. Very accidentally, I pressed on 'Print Screen' and closed. Suddenly, setup melted and gone again. As my experience of 3 times clean installation, if the setup freezes, just press 'Print Screen' and close until setup finishes ):P

Unfortunately, samba share for local computers had got problem. Everyone could read and access any folder or file, but everyone could not upload a file more than 40KB per try. I think it's bug. Need to wait for fix.
Therefore, /etc/init.d/samba is no more available. Instead, use 'sudo restart smbd'.
:KS

---

### Post by neutron68 on 2010-05-05
> **krodrigue said:**
> Go to Applications, Ubuntu Software Center, then in the search box at the top right add samba and you will see...Samba...create, modify, and delete samba shares. That's what you are looking for to add and remove shares.

In Mythbuntu, there is no "Ubuntu Software Center" under the Applications menu.  Note, I mentioned that Mythbuntu uses a different desktop from Gnome.

I take it you DO have this choice in stock Ubuntu (with the Gnome desktop)?

---

### Post by Vegan on 2010-05-06
I run from the coommand prompt...

```
samba
```

and the shell came back with not avaiilable with some suggested packages

```
sudo apt-get istall samba
```

not found

```
sudo apt-get install ssmba4
```
intalling samba4
.....

I had problems so

```
sudo apt-get remove samba4
```

---

### Post by windependence on 2010-05-06
Start      
```
/etc/init.d/samba start
```
Stop      
```
/etc/init.d/samab stop
```
Restart  
```
/etc/init.d/samba restart
```

Your command failed because it was the incorrect syntax.

-Tim

---

### Post by windependence on 2010-05-06
> **CharlesA said:**
> Which version is the old version?

I just checked and it looks like I am running Samba 3.4.7 on 10.04.

That was the one that was installed when I did an apt-get:

```
apt-get install samba
```How did you install Samba 4?
He didn't because it's not even out yet. 3.5.2 is the latest version. 

-Tim

---

### Post by CharlesA on 2010-05-06
Hrm.

An apt-cache search turned up these:

```
charles@thor:~$ apt-cache search samba4
libsamba-hostconfig-dev - Samba host configuration library - development files
libsamba-hostconfig0 - Samba host configuration library
samba4 - LanManager-like file server for Unix (version 4)
samba4-clients - client utilities from Samba 4
samba4-common-bin - Samba 4 common files used by both the server and the client
samba4-dev - tools for extending Samba
samba4-testsuite - test suite from Samba 4
```

I am not going to bother installing it, since I don't want to bork a working machine.


These commands work for the version Samba I am running, since the init.d script has been converted to an upstart job.

```
sudo service smbd start && sudo service nmbd start
```

Stop:
```
sudo service smbd stop && sudo service nmbd stop
```

Restart:
```
sudo service smbd restart && sudo service nmbd restart
```

---

### Post by windependence on 2010-05-06
> **CharlesA said:**
> Hrm.

An apt-cache search turned up these:

```
charles@thor:~$ apt-cache search samba4
libsamba-hostconfig-dev - Samba host configuration library - development files
libsamba-hostconfig0 - Samba host configuration library
samba4 - LanManager-like file server for Unix (version 4)
samba4-clients - client utilities from Samba 4
samba4-common-bin - Samba 4 common files used by both the server and the client
samba4-dev - tools for extending Samba
samba4-testsuite - test suite from Samba 4
```I am not going to bother installing it, since I don't want to bork a working machine.


These commands work for the version Samba I am running, since the init.d script has been converted to an upstart job.

```
sudo service smbd start && sudo service nmbd start
```Stop:
```
sudo service smbd stop && sudo service nmbd stop
```Restart:
```
sudo service smbd restart && sudo service nmbd restart
```
Hmmm....the official SAMBA page doesn't list 4 at all.

Anyway, it's good to see them trying to keep things a but standardized by allowing the "service" command as in Red Hat based distros.

Thanks for the tip!

-Tim

---

### Post by pricetech on 2010-05-06
I got mine working by running smbpasswd.  Pretty simple I know, but in my case it worked.

---

### Post by Vegan on 2010-05-06
I wonder what SAMBA4 is in the repository but it does not replace the version 3.x in the main distribution.

Nothing on the SAMBA.org site either so i I think there is some problem sommewhere I did not notice.

Anyway I thought I would being this to the attention of the community so that I could raise awareness.

):P

---

### Post by Kamilion on 2010-05-18
[http://news.samba.org/developers/Samba_Team_Blog_3/]("http://news.samba.org/developers/Samba_Team_Blog_3/")

[http://wiki.samba.org/index.php/Samba4]("http://wiki.samba.org/index.php/Samba4")

[http://wiki.samba.org/index.php/Samba4/HOWTO]("http://wiki.samba.org/index.php/Samba4/HOWTO")

Samba4 mainly brings native support for Active Directory.
[LIST]
[*]support of the 'Active Directory' logon and administration protocols
[*]new 'full coverage' testsuites
[*]full NTFS semantics for sharing backends
[*]Internal LDAP server, with AD semantics
[*]Internal Kerberos server, including PAC support
[*]Bind9 integration for AD DNS support
[*]new RPC infrastructure (PIDL)
[*]flexible database architecture (LDB)
[*]Python support - used excessively for client and management tools
[*]generic security subsystem (GENSEC)
[/LIST]

They've been working on it since 2004. I've had my eye on it for a while, wanna get rid of my NT4-style primary domain controller.

---

### Post by JedMeister on 2010-06-07
> **Vegan said:**
> I wonder what SAMBA4 is in the repository but it does not replace the version 3.x in the main distribution.

You're right, both Samba3 & Samba4 are in the Lucid repos (actually Samba4 is in Ubuntu since Intrepid - almost 2 years!) All the package details are [here]("http://packages.ubuntu.com/search?keywords=samba4") if you're interested in which specific version etc.

---

