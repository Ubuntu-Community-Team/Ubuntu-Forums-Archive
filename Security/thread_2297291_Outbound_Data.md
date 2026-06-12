---
title: "Outbound Data"
date: 2015-10-02
forum: Security
---

### Post by de Bacon on 2015-10-02
Background:  I really don't know very much about computers, only minimally educated about them due to my age (60+) and interests.  I've been using linux Ubuntu x strictly since 2008 (Hardy).  I use 4 flavors of Ubuntu on a multi boot desktop box with a lot of disc space, multiple drives and partitions.  These are UbuntuStudio 14.04 (default-main), KXStudio 14.04, Kubuntu 12.04 and UbuntuStudio 10.10 ( to utilize some discontinued software).

Problem: The following issue came while using UbuntuStudio 14.04.? (updated daily).
I am noticing data exiting my computer via the ethernet connection.  My noticing this was found using "system monitor," where I sometimes look to see data flow when my isp connection is interrupted or other like conditions occur.  So a few days ago when I looked at System Monitor using the system load tab, I noticed a small amount of outbound signal, short bursts  <6 KiB/s, lasting only a couple of seconds at a time, but repeating regularly within 15 seconds of time elapse.  In considering what was causing this, I started turning thing off, web browser, email program, skype, etc., until all visibly running software was off, to find the out flow continuing.  I rebooted turning only system monitor on and the same outbound data flow occurred.

I then rebooted to a different OS, Kubuntu 12.04.  With that system when turning on System Monitor, there was no outbound data.  I switched back to UbuntuStudio, finding the same.  I figured there must be a compromise somewhere in my system. I looked at and began trying to figure out gufw firewall settings but I am not really understanding that stuff, so concluded that I should re-load the system, and did that yesterday after backing up my critical data. 

After the initial redo and update, I added a few pieces of software including system monitor.  In checking, the leak was seemingly shut off (no data flow outbound).  I added my email (evolution) and imported the backup of it.  Checked again, no outbound data.  My initial thought was, the likely issue was imported through web browsing (firefox, rekonq, or chromium) and that the problem was likely something stored in the .mozilla folder.  So rather than importing my old backup of Firefox, having years of collective bookmarks and potential problems, I decided to start fresh, to recreate the bookmarks as need came. After using Firefox some, I again checked system monitor, finding no outbound data.   I So I then took some of my stored data from a differing HDD and added it to my the OS home directory, checking the system monitor again, and wallah data outbound.  

Scratching my head now, wondering how to isolate this issue.  I then changed the permissions of everything I imported from the other HDD, removing all access to everyone, (I think the numerical equivalent is 000, wher in the gui, it states permissions as “none,” for: owner, group and others.  The leak of data remains.  

Now I am working through a different OS KXStudio where there is no data loss, but this system is strictly designed for audio production and I don't wish to contaminate it through regular usage.  

I took a look at what gufw showed me.  In my testing I found the following.  Reboot &#8594; open only Gnome System Monitor, initially 10 items show up in gufw's “Listening Report.”  I took some screen shot so the content to assist in my analysis.  I noted that if I disconnected the Ethernet connection, the listening report showed 5 items.  When I re-connected the Ethernet, the number jumped to 10, then after a few seconds dropped to 8.  

The following is what this analysis of gufw's Listening report showed.

data source: 
gufw Listening Report
&#8233;The following three items only occur while ethernet is connected.
Added-Note Protocol Port Address Application 
UDP 123 * ntpdate 
* UDP 58566 * dhclient 
UDP 68 * dhclient 
UDP6 123 * ntpdate 
* UDP6 13556 * dhclient 

&#8233;The following items are constant and consistantly showing
Protocol Port Address Application 
UDP 5353 * avahi-daemon 
UDP 54984 * avahi-daemon 
UDP 631 * cups-browsed 
UDP6 5353 * avahi-daemon 
UDP6 53855 * avahi-daemon 
&#8233;* 
The port used changes when reconnecting the system to the ethernet connection


Do you have any ideas or solutions to this issue?  Thanks for reading and any input you might feel inclined to share.

---

### Post by mikewhatever on 2015-10-02
The way [TCP/IP]("https://en.wikipedia.org/wiki/Internet_protocol_suite") works is, some data is sent and some received. There is really no way around it, and there is nothing unusual about the listening precesses.

---

### Post by cariboo on 2015-10-02
Lets have a look at each individual connection:

[LIST]
[*]UDP 123 * ntpdate - this is used to update the time and date on your system
[*]UDP 68 * dhclient  -  this is used to allow a client to connect to a DHCP server. The server would then supply the ip address and any other information the client would need to use the network or to connect to the outside world.
[*]UDP6 123 * ntpdate  - same function as the first item, but using [IPv6]("https://en.wikipedia.org/wiki/IPv6") protocol
[*]UDP 5353 * avahi-daemon - is a zero-configuration networking implementation including multicast service discovery
[*]UDP 631 * cups-browsed - the standard method to broadcast shared networked printers on your local network
[*]UDP6 5353 * avahi-daemon - again same function as the previous daemon except it uses IPv6 networking protocol
[/LIST]

You can disable the avahi-daemon by issuing the following command in a terminal:

```
sudo sh -c "echo manual > /etc/init/avahi-daemon.override"
```

To disable cups, in a terminal issue the following command:

```
sudo echo "manual" > /etc/init/cups.override
```

Disabling ntpdate and dhclient may cause system problems, so I would leave these services alone.

As an aside, these services you see are all standard services enabled in a normal Ubuntu installation, and are nothing to worry about.

---

### Post by de Bacon on 2015-10-02
While I believe you both understand this stuff way better than I, this does not resolve or otherwise my questioning comparatively, why the other system does not act in the same way.    On both the kxstudio and kubuntu systems, after the initial connection with the Ethernet, without additional need/demand, from software the system monitor for input and out of the Ethernet remains consistently flat without data flow in either direction.  This is inconsistent between these differing systems, where as, I would consider that these systems should act equally.  But what would I know. On another note, I never allow the older ubuntu studio 10.10 to see the internet since it is outdated.

Thanks for the inputs.  I now know more than previously, and I appreciate the assist.

---

### Post by bashiergui on 2015-10-02
> I am noticing data exiting my computer via the ethernet connection. My noticing this was found using "system monitor," where I sometimes look to see data flow when my isp connection is interrupted or other like conditions occurLet's define what you mean by "data". If you're looking at system monitor, then you are seeing traffic between your computer and the internet. That doesn't necessarily mean you have your personal or sensitive files leaving your computer. With system monitor you can't tell what is being transferred.

Your gufw output shows more detail, but it is only showing udp connections. Keep in mind that there will be multicasting traffic, too, when the router and your computer chat. Let's look at tcp connections, too. 

Use the terminal command ```
sudo watch ss -ra
```to see what connections your computer has established with the internet. The "watch" part will make the list update automatically every 2 seconds. Most importantly, the ss command will tell you what service is being used. Then you can tell what *kind* of data is being transferred and which direction it's going. If it's updates being automatically downloaded over http from Ubuntu, you probably don't care. If you have a foreign IP connected to your FTP server, then you might be more concerned.

Post the results of the command (remove watch and then you can copy/paste) if you have questions about what you see.

---

### Post by de Bacon on 2015-10-03
bashiergui,

That is a really good command tool!  Thanks for your input, as it did really clear things up for me.  In reviewing the results of that, I didn't see anything in there which enforces my previous  alarm.  I see no need to post the results here.

By the way, I can see both in and out flow of packets with the System Monitor I use.  (System Monitor 3.8.2.1, find it in synaptic) It is not numeric but displayed in a graph, for both in and out traffic.  

Thanks again,

---

### Post by bashiergui on 2015-10-03
> **de Bacon said:**
> By the way, I can see both in and out flow of packets with the System Monitor I use.  (System Monitor 3.8.2.1, find it in synaptic) It is not numeric but displayed in a graph, for both in and out traffic.  

Thanks again,I realized that so I edited my post. The difference between ss and system monitor is ths ss allows you to see exactly what's getting transferred over which protocols. System monitor summarizes the total amount, so it's not specific enough for your purpose.

Glad it helped.

---

### Post by de Bacon on 2016-01-28
Further time has elapsed that has led me to a differing conclusion than the previous conclusion as suggested.  The whole idea of data packets going out of my computer without my intension of sending data out bothered me continually.  I did some experimenting with programs upon a fresh boot which seemed to point out that the data out was sourced from Evolution.  I'd boot up an not open Evolution, noticing that the data flow outbound did not happen.  Then if I opened evolution this data flow would resume.  The timing of it did not coincide with the settings for checking the mail server so I ruled that out.  I did a double check it by disconnecting from the accounts individually (un checking  the profiles in the preferences for each profile) yet once evolution was open, the data packets outbound would continue until I shut down the computer.  Finally I migrated over to Thunderbird, just to see (not a fun process with all the data conversions needed)  the result is this situation no longer happens.  Data packets going out follow what is expected as to the timing of the email client settings and or fetching data from the Internet, when working with a browser.

I am again content, yet I believe this is a security issue that others must be contending with.  

Anyway that is all from here,

---

### Post by bashiergui on 2016-01-28
Would have been easy to solve by capturing the packets during those transfers. Now I'm curious what it was doing.

---

### Post by de Bacon on 2016-01-28
I have no idea what was going or coming.  I don't know how to do capture of packets, but having gone through that switch over, and seeing that the condition is no longer occurring is what gives me a better sense that things are now OKAY, where as before, that was not a truth.

It was small amounts of data being transferred, I quantified it at one time but didn't make a record.  It occurred often enough that a lot of data could be moved over the period of a day.   It was the frequency of packet transfer that really got me to thinking it was some kind of thing I didn't want to happen.   Now when I have both the email client and the browser closed no data moves to or from the net after boot up and the update checks have occurred.  That was not the case before.  

It is done though.  I hope for good!

I guess I can't help resolve your curiosity, nor my own at this point.  Well that may not be true, I still have the evolution email client loaded but disabled and no longer run it.  I was going to make sure I am ready, comfortable with a different email program before full removal.   I do wish that it is not a problem for others though. 

cheers,

---

