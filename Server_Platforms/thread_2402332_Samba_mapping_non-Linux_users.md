---
title: "Samba: mapping non-Linux users"
date: 2018-09-28
forum: Server Platforms
---

### Post by porkpiehat2 on 2018-09-28
Hi all,

I'm fairly new to Samba, so bear with me. I'm trying to map users, but on the way I'm running into some difficulties.

I have a Raspberry Pi 3 running Raspbian Stretch (up-to-date) and Samba 4.5 to share an external hdd. There are two shares configures, a public and private. The public one has (read-only) access for all devices in the network, e.g. media streamers. The private share should only be accessible by a few selected devices.
Now here's the catch: these devices are all non-Linux (Windows 7/10 and Android). Since I trust these devices, I want to grant them access without a password prompt.

I looked into mapping these devices to a user based on their MAC- or IP-address, but that seems impossible just from smb.conf. My alternative is to map the users to an "admin"-user, using the "username map" option. For this, however, I need to find out with which usernames my devices connect to set up the mapping.
I attempted to set device-specific logging, increase the verbosity to level 2, and see what pops up.

Few interesting observations:
[LIST]
[*]The logs are stored as log.[IP], although older log still show log.[devicename]. I assume this has to do with the parameters "wins server" and "dns proxy", though I have not really understood these.. (any help please? Would be a lot easier if they resolve with devicename)
[*]For my laptop, I see two logs: log.[IP] and log.[name]. For my phone, I only get log.[IP].
[*]The log.[IP] of my laptop shows two interesting lines: "Authentication for user [devicename] FAILED." And just below that, "Authentication for user [username] FAILED." In the usermap I tried mapping either of these two to the user "pi" (default R-Pi user), no luck.
[*]The logs of my phone only show Guest as user, no device-specific username. Should I increase verbosity to see the actual username?
[/LIST]

What are your thoughts on this? I'm happy to hear any suggestions, I want to understand this better.

---

### Post by Morbius1 on 2018-09-28
> The private share should only be accessible by a few selected devices.
> I looked into mapping these devices to a user based on their MAC- or IP-address, but that seems impossible just from smb.conf.
Um .... how about something like this:

[1] Make the share Public

[2] But make it accessible only to those devices.

Something like this:
```
[Share]
path = /path/to/Share
guest ok = yes
read only = no
hosts allow = 192.168.0.105, 192.168.0.108, 192.168.0.110

```
192.168.0.105 would be your WIn10 box.
192.168.0.108 would be your Android
192.168.0.110 would be your Interocitor

---

### Post by porkpiehat2 on 2018-09-28
Right.. That is a simple solution. How come this did not pop up in the Google search results when I looked for IP-, host- and what-not-access?
For this part it works. With the "force user" added, I have read/write permissions to all files in the private share from all devices. Perfect*. :)

The other part that I wanted to achieve with mapping the users is that these selected devices have read/write-access to the public share too. In the case of users, it would simply be "write list = admin". With the "hosts allow" parameter, I found [this solution]("https://unix.stackexchange.com/questions/75770/how-to-give-read-write-permissions-using-ips-in-samba") to give r/w access to the selected hosts, but it doesn't seem to work for me yet. The device with IP 192.168.1.101 now requires a password to access (this is a Linux device, coincidentally). This is the relevant part of the config-file:

```

[NAS1-Public]
comment = Public share
path = /media/NAS1/Public
browseable = yes
guest ok = yes
public = yes
read only = yes
hosts allow = 192.168.1.101, 192.168.1.106/200

[NAS1-Public]
comment = Public share R/W
path = /media/NAS1/Public
browseable = yes
public = yes
writeable = yes
force user = pi
hosts allow = 192.168.100/105 EXCEPT 192.168.1.101

```

Thanks a lot for the input so far!

[SIZE=2]* I realise this is not the safest option. But since they have static IPs based on their mac-addresses, and they all have passwords to access, I consider it safe enough for home use.[/SIZE]

---

### Post by Morbius1 on 2018-09-29
It's OK to have two share definitions to the same path. What is not OK is for both of them to have the same share name. Change the second Public share definition to something like this:
> [NAS1-Public[COLOR=#0000cd]**Admin**[/COLOR]]
comment = Public share R/W
path = /media/NAS1/Public
browseable = yes
public = yes
writeable = yes
force user = pi
hosts allow = 192.168.100/105 EXCEPT 192.168.1.101

---

### Post by porkpiehat2 on 2018-10-01
> **Morbius1 said:**
> It's OK to have two share definitions to the same path. What is not OK is for both of them to have the same share name.

Interesting.. The Stackexchange-answer that I linked before actually does state as solution to use two identically-named share definitions with different allowed hosts. The answer was recent too, so I guess this is not something that has changed in Samba in the past months.
I'll play around with it a bit more still and let you know. Preferably I stick to one share name, makes it easier for my partner ;)

The other question, about resolving the hostnames and the WINS server and DNS Proxy parameters. I tried reading up on it, but to me its not fully clear what they do. Can someone briefly explain?

---

### Post by Morbius1 on 2018-10-01
> **porkpiehat2 said:**
> Interesting.. The Stackexchange-answer that I linked before actually does state as solution to use two identically-named share definitions with different allowed hosts. The answer was recent too, so I guess this is not something that has changed in Samba in the past months.
I'll play around with it a bit more still and let you know. Preferably I stick to one share name, makes it easier for my partner ;)
You don't have to take my word for it you can verify it for yourself.

I added your two share definitions to my own smb.conf, saved the file, then ran the smb.conf interpreter:
```
testparm -s
```
Only the second [NAS1-Public] shows up:
> [NAS1-Public]
    comment = Public share R/W
    force user = pi
    guest ok = Yes
    hosts allow = 192.168.100/105 EXCEPT 192.168.1.101
    path = /media/NAS1/Public
    read only = No
Samba reads smb.conf to find changes to the default settings. When it does that it reads the file from top to bottom from service definition to service definition. If a parameter or a service definition is repeated the last one encountered will be the one that is used.

A WINS server can be used for netbios name resolution but it has to be set up. One machine has to be designated as the WINS server, it has to have a static ip address, all the other machines have to be configured to point to that ip address as the WINS server, and it can never be turned off. Haven't done this in years. As far as the dns proxy thingy haven't ever used it so I don't know.

In a modern home network name resolution is best handled with static ip addresses ( no name resolution ), mDNS ( Win10, Linux, and macOS can do that ), and if all else fails by the old netbios broadcast mechanism which won't work on the client side in Ubuntu 18.04 - at least not by default.

[COLOR=#0000cd]**EDIT**[/COLOR]: That last sentence is not accurate. The broadcast mechanism can be used for name resolution on the Ubuntu 18.04 client. What the Ubuntu 18.04 client cannot do is utilize netbios broadcast to "discover" hosts by name. It has to be done explicitly.

---

