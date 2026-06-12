---
title: "Ubuntu server uptime is low, how to make it higher?"
date: 2011-12-20
forum: Server Platforms
---

### Post by Gordon2011 on 2011-12-20
Hi All:

My Ubuntu server uptime is less than 96%. How to make it greater than 99%?

Many thanks,
Gordon

---

### Post by Bachstelze on 2011-12-20
Don't turn it off.

*EDIT:* Also why is this in FF&H?

---

### Post by Gordon2011 on 2011-12-20
> **Bachstelze said:**
> Don't turn it off.

*EDIT:* Also why is this in FF&H?
Thank you. How can I know the server was turned off? Actually I did not turn it off manually in the last 24 hours. But an online monitoring software show that its uptime is just 95% in the last 24 hours. 

Gordon

---

### Post by CharlesA on 2011-12-20
Moved to Cafe.

What are you using to show your uptime?

I just use uprecords on my Ubuntu box:

```
charles@Lucid:~$ uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    46 days, 06:22:29 | Linux 2.6.32-33-generic   Sun Aug 28 08:58:07 2011
     2    26 days, 06:08:14 | Linux 2.6.32-34-generic   Fri Oct 14 05:10:14 2011
     3    22 days, 21:13:44 | Linux 2.6.32-35-generic   Wed Nov  9 10:21:18 2011
     4    22 days, 20:28:26 | Linux 2.6.32-33-generic   Fri Aug  5 12:09:23 2011
     5    21 days, 09:55:14 | Linux 2.6.32-32-generic   Thu Jun 16 21:11:55 2011
     6    19 days, 15:54:09 | Linux 2.6.32-33-generic   Sat Jul 16 19:43:23 2011
     7    14 days, 22:23:22 | Linux 2.6.32-36-generic   Sun Dec  4 13:18:36 2011
     8     8 days, 12:34:44 | Linux 2.6.32-32-generic   Fri Jul  8 07:04:42 2011
     9     1 day , 04:54:16 | Linux 2.6.32-35-generic   Sat Dec  3 08:24:08 2011
->  10     1 day , 02:12:38 | Linux 2.6.32-37-generic   Mon Dec 19 11:42:11 2011
----------------------------+---------------------------------------------------
1up in     0 days, 02:41:39 | at                        Tue Dec 20 16:33:54 2011
no1 in    45 days, 04:09:52 | at                        Fri Feb  3 18:02:07 2012
    up   185 days, 02:13:33 | since                     Thu Jun 16 21:08:11 2011
  down     1 day , 15:33:05 | since                     Thu Jun 16 21:08:11 2011
   %up               99.118 | since                     Thu Jun 16 21:08:11 2011

```

---

### Post by LowSky on 2011-12-20
maybe you lost your internet connection?

---

### Post by Gordon2011 on 2011-12-20
> **CharlesA said:**
> Moved to Cafe.

What are you using to show your uptime?

I just use uprecords on my Ubuntu box:

```
charles@Lucid:~$ uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    46 days, 06:22:29 | Linux 2.6.32-33-generic   Sun Aug 28 08:58:07 2011
     2    26 days, 06:08:14 | Linux 2.6.32-34-generic   Fri Oct 14 05:10:14 2011
     3    22 days, 21:13:44 | Linux 2.6.32-35-generic   Wed Nov  9 10:21:18 2011
     4    22 days, 20:28:26 | Linux 2.6.32-33-generic   Fri Aug  5 12:09:23 2011
     5    21 days, 09:55:14 | Linux 2.6.32-32-generic   Thu Jun 16 21:11:55 2011
     6    19 days, 15:54:09 | Linux 2.6.32-33-generic   Sat Jul 16 19:43:23 2011
     7    14 days, 22:23:22 | Linux 2.6.32-36-generic   Sun Dec  4 13:18:36 2011
     8     8 days, 12:34:44 | Linux 2.6.32-32-generic   Fri Jul  8 07:04:42 2011
     9     1 day , 04:54:16 | Linux 2.6.32-35-generic   Sat Dec  3 08:24:08 2011
->  10     1 day , 02:12:38 | Linux 2.6.32-37-generic   Mon Dec 19 11:42:11 2011
----------------------------+---------------------------------------------------
1up in     0 days, 02:41:39 | at                        Tue Dec 20 16:33:54 2011
no1 in    45 days, 04:09:52 | at                        Fri Feb  3 18:02:07 2012
    up   185 days, 02:13:33 | since                     Thu Jun 16 21:08:11 2011
  down     1 day , 15:33:05 | since                     Thu Jun 16 21:08:11 2011
   %up               99.118 | since                     Thu Jun 16 21:08:11 2011

```


[FONT=PrimaSans BT,Verdana,sans-serif]The monitoring service, MONITIS,[/FONT] is used to show the uptime. I am trying to find the reason. 

Thank you,
Gordon

---

### Post by Gordon2011 on 2011-12-20
> **LowSky said:**
> maybe you lost your internet connection?

I hope it is the reason. So how can I confirm it and solve the problem? 

Many thanks,
Gordon

---

### Post by CharlesA on 2011-12-20
> **Gordon2011 said:**
> I hope it is the reason. So how can I confirm it and solve the problem? 

Many thanks,
Gordon
You would have to confirm how they monitor uptime and then go from there.

You can also install uprecords on the box to keep track of your uptime:

```
sudo apt-get install uptimed
```

---

### Post by Bachstelze on 2011-12-20
Off-topic, but...

> My philosophy - use whatever works for you, be it *nix, OSX or Windows.

You know OS X *is* *nix, right?

---

### Post by CharlesA on 2011-12-20
> **Bachstelze said:**
> Off-topic, but...



You know OS X *is* *nix, right?
It's BSD-based.

---

### Post by Gordon2011 on 2011-12-20
> **CharlesA said:**
> You would have to confirm how they monitor uptime and then go from there.

You can also install uprecords on the box to keep track of your uptime:

```
sudo apt-get install uptimed
```

Thank you. I will try it and let you know the result.
Gordon

---

### Post by tgalati4 on 2011-12-20
My Dapper desktop (but now used as a server) has been up for 99.9917% (down about 4 hours in 5.5 years).


tgalati4@tubuntu2:~$ uprecords
     #               Uptime | System                                    Boot up 
----------------------------+-------------------------------------------------
->   1   220 days, 08:37:06 | Linux 2.6.15-57-386      Sat May 14 10:55:07 2011
     2   216 days, 06:49:56 | Linux 2.6.15-28-386      Tue May 22 22:36:24 2007
     3   187 days, 00:54:23 | Linux 2.6.15-55-386      Sat Jun 26 14:31:39 2010
     4   163 days, 23:49:22 | Linux 2.6.15-26-386      Tue Oct 24 12:19:49 2006
     5   153 days, 01:33:24 | Linux 2.6.15-29-386      Wed Dec 26 13:22:27 2007
     6   117 days, 23:40:07 | Linux 2.6.15-51-386      Thu Jun  7 10:18:37 2007
     7    94 days, 02:31:54 | Linux 2.6.15-52-386      Mon Oct 20 10:55:37 2008
     8    64 days, 20:48:44 | Linux 2.6.15-54-386      Sun Aug  2 12:56:44 2009
     9    59 days, 15:24:32 | Linux 2.6.15-53-386      Sun Feb  8 16:44:19 2009
    10    44 days, 22:39:39 | Linux 2.6.15-55-386      Sat Oct 24 10:56:14 2009
----------------------------+-------------------------------------------------

---

