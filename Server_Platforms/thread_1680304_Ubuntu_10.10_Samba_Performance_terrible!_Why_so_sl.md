---
title: "Ubuntu 10.10 Samba Performance terrible! Why so slow?"
date: 2011-02-02
forum: Server Platforms
---

### Post by sentinelace on 2011-02-02
I recently upgraded to Ubuntu 10.10.  Everyone was working fine in 10.04 samba related.  Now when I simply try to browse the network, it's terrible.  Very slow.  I also noticed when I try to login to the server, it's slow.  Maybe this is a network card issue?  I recall having to change speeds in the past to fix a similar issue.  Any one else having this problem?

---

### Post by WinstonChurchill on 2011-02-03
> **sentinelace said:**
> I recently upgraded to Ubuntu 10.10.  Everyone was working fine in 10.04 samba related.  Now when I simply try to browse the network, it's terrible.  Very slow.  I also noticed when I try to login to the server, it's slow.  Maybe this is a network card issue?  I recall having to change speeds in the past to fix a similar issue.  Any one else having this problem?
Best solution: use FTP - it's faster, more reliable, and probably more secure. I'd suggest vsftpd - I regularly get 100+ MB/s on my LAN transfers, and I don't have any networking hardware that cost more than $30.

Remember that Windows (and Samba) default to using broadcasting to find computers on the network, which for obvious reasons sucks. The normal solution would be to run a WINS server, but who wants to do that? Easy fix: use domain names or IP addresses instead of NetBIOS names (eg, instead of "\\ComputerName" use \\x.x.x.x, or "\\ComputerName.yourdomain" if you have a DNS server). As far as file transfers go, Samba just isn't that fast.

---

### Post by sentinelace on 2011-02-03
That is not a solution to a network. I have apps that need to write to a samba share. I am already running a WINS server. The performance sucks regardless of using IP's or netbios names.  It may have never been fast, but when I simply try to browse a samba share, I get "not responding" and rarely can even make it within a folder.

---

### Post by dtfinch on 2011-02-03
Are you accessing it from Windows or Linux? And are large file copies slow too, and if so, how slow and in both directions?

If file copies are fast in both directions. I'd lean towards a name resolution issue. Windows and Linux will both try DNS before trying WINS.

If the speed is around the 100kb/s range or slower, I'd say it was a network issue, especially if it's faster in one direction. We've had various combinations of gigabit cards, switches, and drivers cause this.

If your clients are Windows, there's a WebClient service that can sometimes cause delays, especially if port 80 on the server is blocked. When enabled, Windows tries to connect to every server as a WebDav server first, only trying SMB/CIFS when that fails. If you don't use Windows' built-in WebDav support (almost nobody does), you could try disabling that.

I don't know what's changed between 10.04 and 10.10 that could also cause such slowness.

---

### Post by sentinelace on 2011-02-03
hmm.  Odd thing is, everything seems to work flawless in windows 2000.  I haven't tested xp.  Maybe something to do with windows 7?  I thought I read of people having issues with this.  Now the other odd thing is, everything works fine when I connect to my redhat server, but not the ubuntu server.  Speed is so bad, it locks up my computer.  So I am accessing from Windows 7 to the samba share on the ubuntu server.

---

### Post by dtfinch on 2011-02-03
There is this huge thread of people having slow network share performance with Windows 7, but no real answers that I could see:
[http://social.technet.microsoft.com/Forums/en-US/w7itproperf/thread/4537c7b6-9761-41c5-8b47-0ecb831c8575](http://social.technet.microsoft.com/Forums/en-US/w7itproperf/thread/4537c7b6-9761-41c5-8b47-0ecb831c8575)

My only personal experience with Windows 7 and Samba slowness was when copying a lot of large files, my transfer speed increased about 5x when I disabled MS Security Essentials. But your problems sound like something else.

---

### Post by elico on 2011-02-03
yes thers is something...
there are coupele of thigs about wins and windows 7\vista and samba 3.x and shares.
on windows vista and 7 there is a new thing for name service and you can find the name of the protocol using wireshark.
i found it make loookups very slow on network.
also you can look the nsswitch file in ubuntu server that makes the hosts and dns lookups order..
hosts ..>dns>wins
there is a bug about the samba wins that works slow a hell.
also in resolve.conf on ubuntu machine you might have domain and search settings that you can try to comment and see if it makes things better.
i am accesing windows vista and 7 to ubuntu samba and it works fine after making these things right.

---

### Post by jstaffon on 2011-02-05
I don't think it's just Ubuntu 10.10. I have an Ubuntu 10.04 and a Suse 11.3 linux box. I've done testing with both machines writing to a NAS box on my gigabit network. Both of them run around 2 to 3 MB/s. If I startup my Windows 7 box and transfer the same file to the NAS box, it runs at 80 MB/s. I've tried all kinds of Samba tuning hints but just can't get the performance even close to the Windows 7 box. If I export the filesystem and mount the NAS using NFS, I get around 80 MB/s. That tells me it's not the network or the NAS box. I'm not running WINS either on my network. I don't believe you need that. All my machines have static IPs and reside in all the hosts files. Any help would be much appreciated.
Jeff.

---

### Post by sentinelace on 2011-02-09
Still having this issue.  I found a thread about adjust the MTU on my network card but issue remains.  Now what?

---

### Post by arrrghhh on 2011-02-09
> **sentinelace said:**
> Still having this issue.  I found a thread about adjust the MTU on my network card but issue remains.  Now what?

Have you tried other solutions like the one listed above?

If another protocol is fast (like NFS) you can start narrowing it down.  At this point it could almost be anything - between the NIC settings, the switchport settings, etc.

---

### Post by sentinelace on 2011-02-16
Is there a good guide for mounting NFS shares?  Seems to be a pain and I'll have to install Window Unix Services on every pc on my network...

---

### Post by arrrghhh on 2011-02-16
> **sentinelace said:**
> Is there a good guide for mounting NFS shares?  Seems to be a pain and I'll have to install Window Unix Services on every pc on my network...

NFS doesn't work on Windows out of the box.  I recommend NFS for Linux/Unix boxes, SMB for Winblows.

I was simply suggesting trying a different protocol to help triage the issue - to see if it's the box, or the protocol.

---

### Post by sentinelace on 2011-02-16
well I am trying to connect a windows 7 box to a Ubuntu Samba share so I need smb to work!

---

### Post by arrrghhh on 2011-02-16
> **sentinelace said:**
> well I am trying to connect a windows 7 box to a Ubuntu Samba share so I need smb to work!

...I was trying to narrow it down.  If you don't want to take my suggestion, it's going to be much, **MUCH** harder to determine what the actual problem is - because you basically have refused to rule out the box or the network.  Without ruling those out, looking into particular issues with samba would be pointless.

This is troubleshooting - you have to look at all angles to see where the actual source of the problem is.  If it's your network, then there's nothing wrong with samba or the box.  If it's the box, then we can determine what that problem is - duplex settings perhaps.  There are too many variables, we need to eliminate as many as we can!

---

### Post by sentinelace on 2011-02-16
Well samba functions perfect if I access the smb share from a windows 2000 box.  It's only from XP and windows 7 that it doesn't work.  I will try NFS but it's not a good perm. solution.  Wasn't trying to be rude.

---

### Post by arrrghhh on 2011-02-16
> **sentinelace said:**
> Well samba functions perfect if I access the smb share from a windows 2000 box.  It's only from XP and windows 7 that it doesn't work.  I will try NFS but it's not a good perm. solution.  Wasn't trying to be rude.

I apologize, I might need to re-read the thread - I didn't realize that a Win2k box worked fine with samba.

If that's the case, the problem lies with your XP/7 boxes - you'll need to figure out what's different on them besides the OS.  Different network, subnet, network settings, etc.  If the problem is not with samba or the Ubuntu box, I'm not really sure how we can help in an Ubuntu forum... Your issue sounds like it's a problem with your Windows boxes.

We will do our best to help you isolate the issue, I'm just saying that if the issue is indeed with the Windows machines asking in an Ubuntu forum might not be so productive...

---

### Post by sentinelace on 2011-02-25
The probelm is it is with all windows 7 machines. Is there no fix? I see issues all over the net with vista/7 connecting to a samba share. Weird thing is, it worked fine in previous versions of ubuntu and works in redhat just fine.
 
Edit: I have disabled SMB 2.0 which vista and windows 7 uses and so far it's working perfect!!!  I'll keep this thread OPEN so I can further test.

---

### Post by arrrghhh on 2011-02-25
> **sentinelace said:**
> Edit: I have disabled SMB 2.0 which vista and windows 7 uses and so far it's working perfect!!!  I'll keep this thread OPEN so I can further test.

My neighbor was complaining about how slow his laptop pulls stuff from my server, and he has a new 7 laptop... never really occurred to me that it was samba, I just blamed it on the cheapo broadcom wlan card :p.

I'll try this and see if it makes any difference.

---

### Post by sentinelace on 2011-02-25
to disable SMB 2.0, open a CMD prompt and paste the following:
 
```

sc config lanmanworkstation depend= bowser/mrxsmb10/nsi 

```
 
then:
 
```

sc config mrxsmb20 start= disabled 

```
 
To enable SMB 2.0:
 
```

sc config lanmanworkstation depend= bowser/mrxsmb10/mrxsmb20/nsi 

```
 
Then:
```

sc config mrxsmb20 start= auto 

```

---

### Post by dtfinch on 2011-02-25
Here's someone with similar slow transfer rates, but it goes away when they connect by IP rather than server name, which seems odd but it might be worth testing:
[http://superuser.com/questions/247354/why-is-smb-from-a-windows-7-64-bit-to-os-x-server-so-slow-when-using-dns-vs-ip](http://superuser.com/questions/247354/why-is-smb-from-a-windows-7-64-bit-to-os-x-server-so-slow-when-using-dns-vs-ip)

edit: Posted before seeing that disabling smb2 fixed it.

---

### Post by sentinelace on 2011-02-25
by ip didn't matter for me.  Disabling SMB 2.0 is working so far.

---

### Post by arrrghhh on 2011-02-25
> **sentinelace said:**
> by ip didn't matter for me.  Disabling SMB 2.0 is working so far.

I'm already going by IP.  Thanks for the instructions on disabling SMB 2.0, have you noticed any side-effects?

---

### Post by sentinelace on 2011-02-25
not yet... knocking on wood :guitar:

---

### Post by sentinelace on 2011-03-03
well I think I spoke too soon.  Back to slow again.  Doesn't make any sense.  I haven't done the smb disable on the DC yet.  Should I?

---

### Post by arrrghhh on 2011-03-04
> **sentinelace said:**
> well I think I spoke too soon.  Back to slow again.  Doesn't make any sense.  I haven't done the smb disable on the DC yet.  Should I?

I tried this "fix" and it did nothing on my neighbor's Win7 machine.

His was fast at first (AFAIK), and "something" happened to his computer.  Can't really tell what happened, other than he might've caught a virus.  No other user on the network is having the issue...

---

### Post by Foeburner on 2011-04-07
This thread cant be dead yet! I am also having the same issue. Mines started with 10.04 (or at least when I noticed it) and then I upgraded to 10.10 with the issue still persisting. 

Funny thing is that my win7 box works sorta fine. I can write at 2-3Mbps! Only our Vista boxes are having this issue where it freezes when accessing. 

I used to be able to write at 25Mbps before.

typing that cmd didnt work for me either

---

### Post by gobbledigook on 2011-04-07
i too do hope some other solution arises... 

My issue with samba is that **getting** the dir listings is sooooo slow!! it is lightening fast from my xp box to my 10.10 server... but from my 10.10 netbook to my server takes 30 sec + everytime i click on a damned dir!! and yes... both machines are in the same workgroup

---

### Post by sentinelace on 2011-04-07
For some reason mine does work when I do everything by IP instead of name

---

### Post by arrrghhh on 2011-04-07
> **sentinelace said:**
> For some reason mine does work when I do everything by IP instead of name

I have it thru IP, and it's still painfully slow.

It seems to be an issue with Win7, I tested a machine that was running 7 and now is back on XP - issue was present in 7, but not in XP... Might just be this particular machine, YMMV.

---

### Post by RansomStark on 2011-08-23
Resolved my slow windows 7 to linux samba speed via this link

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/3347eddf-e826-409c-972d-9587ac92d9f0](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/3347eddf-e826-409c-972d-9587ac92d9f0)

read last post

> 
Resolved my issue by doing the following from a command prompt

 

c:\windows\system32\netsh interface tcp set global autotuning=disabled

and removing "remote differential compression. See article here:

[http://www.sysprobs.com/windows-7-network-slow](http://www.sysprobs.com/windows-7-network-slow)


---

