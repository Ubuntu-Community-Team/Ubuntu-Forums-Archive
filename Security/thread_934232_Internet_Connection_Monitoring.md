---
title: "Internet Connection Monitoring"
date: 2008-09-30
forum: Security
---

### Post by shqip on 2008-09-30
Is there any solution or program to stop [COLOR=DarkRed]Microsoft/akamai/yahoo[/COLOR] and its partners from keep sending and receiving pocket data to me. I have blocked their ip addresses on my firewall but that don't seem to have had any effect on them. They go right through it and keep sending/receiving data. 
My internet connection is always being monitored by them and a lot of other sales companies. Here is a screen shot of only 2 which is Microsoft and yahoo monitoring my connection  constantly and from time to time they do a port scan. Thank you.

---

### Post by jms1989 on 2008-09-30
Hmm, do have them blocked on your inbound connections? Connection made to you from a remote host. Do you have a hardware-based firewall, like a router, in place? Install or launch firestarter to try to block them.

---

### Post by shqip on 2008-09-30
> **jms1989 said:**
> Hmm, do have them blocked on your inbound connections? Connection made to you from a remote host. Do you have a hardware-based firewall, like a router, in place? Install or launch firestarter to try to block them.
[SIZE=3]Yes I do have a very good hardware-based firewall and  I have also blocked their IP addresses but they still go right through without any problems it seems.  I have firestarter installed but they don't seem to make much difference on professional program writers, wmasters and network masters. There must be another program out there to be  able to stop them. [/SIZE]

---

### Post by cdenley on 2008-09-30
> **shqip said:**
> [SIZE=3]Yes I do have a very good hardware-based firewall and  I have also blocked their IP addresses but they still go right through without any problems it seems.  I have firestarter installed but they don't seem to make much difference on professional program writers, wmasters and network masters. There must be another program out there to be  able to stop them. [/SIZE]
You probably won't get much help with your hardware firewall, but there is not any reason why you wouldn't be able to block any traffic using iptables. That image you posted looks like it is for outgoing traffic.
```

sudo iptables -A OUTPUT -d 66.163.181.177 -j DROP
sudo iptables -A OUTPUT -d 207.46.111.60 -j DROP
sudo iptables -A INPUT -s 66.163.181.177 -j DROP
sudo iptables -A INPUT -s 207.46.111.60 -j DROP

```

---

### Post by shqip on 2008-09-30
> **cdenley said:**
> You probably won't get much help with your hardware firewall, but there is not any reason why you wouldn't be able to block any traffic using iptables. That image you posted looks like it is for outgoing traffic.
```

sudo iptables -A OUTPUT -d 66.163.181.177 -j DROP
sudo iptables -A OUTPUT -d 207.46.111.60 -j DROP
sudo iptables -A INPUT -s 66.163.181.177 -j DROP
sudo iptables -A INPUT -s 207.46.111.60 -j DROP

```
That code is great.. thank you...  
 -do you know the code for dropping ips: example: 207.46.0.0 &#8211; 207.46.255.255 or do I use the same code and where do I see the results in this case that these ips have been blocked. Thank you

---

### Post by cdenley on 2008-09-30
> **shqip said:**
> That code is great.. thank you...  
 -do you know the code for dropping ips: example: 207.46.0.0 &#8211; 207.46.255.255 or do I use the same code and where do I see the results in this case that these ips have been blocked. Thank you

```

sudo iptables -A OUTPUT -d 207.46.0.0/16 -j DROP
sudo iptables -A INPUT -s 207.46.0.0/16 -j DROP

```
By the way, if you're not familiar with iptables, these rules will not be persistent. When you reboot your computer, they will be lost. I'm just trying to demonstrate that if what you have been doing wasn't filtering the traffic, you simply weren't doing right.

If you want to see your firewall rules
```

sudo iptables -L -n

```

If you want to see traffic going to/from your computer, use tcpdump.
```

sudo apt-get install tcpdump
man tcpdump
sudo tcpdump

```

If you want to see what TCP connections are currently open
```

sudo netstat -tpn

```

---

### Post by Dr Small on 2008-09-30
> **shqip said:**
> 
 -do you know the code for dropping ips: example: 207.46.0.0 – 207.46.255.255 or do I use the same code and where do I see the results in this case that these ips have been blocked. Thank you

That is called an IP Range. You would probably want to block the range: 207.46.0.0/16

---

### Post by shqip on 2008-09-30
> **cdenley said:**
> ```

sudo iptables -A OUTPUT -d 207.46.0.0/16 -j DROP
sudo iptables -A INPUT -s 207.46.0.0/16 -j DROP

```
By the way, if you're not familiar with iptables, these rules will not be persistent. When you reboot your computer, they will be lost. I'm just trying to demonstrate that if what you have been doing wasn't filtering the traffic, you simply weren't doing right.

If you want to see your firewall rules
```

sudo iptables -L -n

```

If you want to see traffic going to/from your computer, use tcpdump.
```

sudo apt-get install tcpdump
man tcpdump
sudo tcpdump

```

If you want to see what TCP connections are currently open
```

sudo netstat -tpn

```
Thank you this is great, but I wanted it to be saved so I don't have to enter the same IP addresses all the time I reboot.

---

### Post by shqip on 2008-09-30
> **Dr Small said:**
> That is called an IP Range. You would probably want to block the range: 207.46.0.0/16
Why not? That IP range  belongs to Microsoft. There are certain hosting web designing, internet providers, some sales, and a lot of networking companies that try to get all sort of info out of you and I like my privacy...that's what i wanted to block their IP rage.

---

### Post by cdenley on 2008-09-30
> **shqip said:**
> Thank you this is great, but I wanted it to be saved so I don't have to enter the same IP addresses all the time I reboot.

If you want to use iptables directly, you can make your current rules persistent by doing something like this
```

sudo -s
iptables-save>/etc/iptables.rules
echo \#\!/bin/sh>/etc/network/if-up.d/iptables
echo "iptables-restore</etc/iptables.rules">>/etc/network/if-up.d/iptables
chmod 755 /etc/network/if-up.d/iptables
exit

```
I haven't tested this, so let me know if it works properly. Most people use frontends for iptables like ufw, firestarter, or guarddog. I'm not sure which of those will filter outgoing connections (I never use frontends).

---

### Post by Dr Small on 2008-09-30
> **shqip said:**
> Why not? That IP range  belongs to Microsoft. There are certain hosting web designing, internet providers, some sales, and a lot of networking companies that try to get all sort of info out of you and I like my privacy...that's what i wanted to block their IP rage.
I think you misread my post; Please go back and read it again.

---

### Post by shqip on 2008-09-30
> **cdenley said:**
> If you want to use iptables directly, you can make your current rules persistent by doing something like this
```

sudo -s
iptables-save>/etc/iptables.rules
echo \#\!/bin/sh>/etc/network/if-up.d/iptables
echo "iptables-restore</etc/iptables.rules">>/etc/network/if-up.d/iptables
chmod 755 /etc/network/if-up.d/iptables
exit

```
I haven't tested this, so let me know if it works properly. Most people use frontends for iptables like ufw, firestarter, or guarddog. I'm not sure which of those will filter outgoing connections (I never use frontends).
I did and i tried to find the all IP's I entered when I rebooted but couldn't...

---

### Post by shqip on 2008-09-30
> **Dr Small said:**
> I think you misread my post; Please go back and read it again.
You said:... &#8220;that is called an IP range. You wouldn't probably want to block the range: 207.46.0.0/16&#8221;
 

 I said:.. &#8220; why not? That IP range is Microsofts&#8221;.  
 I don't see what exactly did I misread! 

   	 	 	 	 	 	  I intended to block Microsoft and IPz they and some other use.

---

### Post by Dr Small on 2008-09-30
> **shqip said:**
> You said:... “that is called an IP range. You **_wouldn't_** probably want to block the range: 207.46.0.0/16”

 I don't see what exactly did I misread! 

I ask you to read, one more time. Also notice, if you will take the time to do, I have **not** edited my original post, nor the following quote.

> **Dr Small said:**
> That is called an IP Range. You **_would_** probably want to block the range: 207.46.0.0/16

;)

---

### Post by shqip on 2008-09-30
> **Dr Small said:**
> I ask you to read, one more time. Also notice, if you will take the time to do, I have **not** edited my original post, nor the following quote.



;)
oh my i need glasses i think ...sorry... misread it. apologies.

---

### Post by shqip on 2008-09-30
You know i've been doing a few things at the same time.:confused:. that could have been the reason I misread it twice

---

### Post by -grubby on 2008-09-30
Just a question.. why is your screenshot in an odt file?

---

### Post by shqip on 2008-09-30
> **nathangrubb said:**
> Just a question.. why is your screenshot in an odt file?
when i resized it and more visible i transferred and saved it into odt file

---

### Post by lovinglinux on 2008-10-01
You should give [COLOR="Red"]**[Moblock]("http://moblock-deb.sourceforge.net/")**[/COLOR] a try. It has a Microsoft IP blocklist enabled by default, provided by Bluetack (along with other lists). You can even create your own blocklists or add more from other sources. If you also install mobloquer you can enable/disable/add/remove blocklists using a GUI and allow specific services ( HTTP/HTTPS/FTP/POP...) or IP's to bypass the block.

I guess this is what you are looking for.

The only thing you should be careful is starting moblock/mobloquer after Firestarter, otherwise it won't block anything.

---

### Post by shqip on 2008-10-01
Thank you. I'll try MoBlock, but it seems that I have a problem with the third party software sources.  
 I cannot add this link “[http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian)” on the software source!!! it does  not allow me. Anybody know what this could be and how I might add that link. I have attached a screen shot...

---

### Post by cdenley on 2008-10-01
> **shqip said:**
> Thank you. I'll try MoBlock, but it seems that I have a problem with the third party software sources.  
 I cannot add this link “[http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian)” on the software source!!! it does  not allow me. Anybody know what this could be and how I might add that link. I have attached a screen shot...

Did you try reading the screen capture you pasted? The input text should be
```

deb http://moblock-deb.sourceforge.net/debian hardy main

```

---

### Post by The Cog on 2008-10-01
You are missing the keyword deb at the front of the line. I'm not sure if a section name like **hardy** is needed at the end of the line too.

Oops - beaten to it - by a better answer too.

---

### Post by shqip on 2008-10-01
> **cdenley said:**
> Did you try reading the screen capture you pasted? The input text should be
```

deb http://moblock-deb.sourceforge.net/debian hardy main

```
Thank you guys...it's all done now. I am  trying to find the code to add  those IP ranges/addresses I want to block.

---

### Post by shqip on 2008-10-01
> **The Cog said:**
> You are missing the keyword deb at the front of the line. I'm not sure if a section name like **hardy** is needed at the end of the line too.

Oops - beaten to it - by a better answer too.
thanks. it is done now

---

