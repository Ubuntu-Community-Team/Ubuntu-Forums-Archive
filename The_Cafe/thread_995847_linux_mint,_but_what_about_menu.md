---
title: "linux mint, but what about menu?"
date: 2008-11-28
forum: The Cafe
---

### Post by uberdonkey5 on 2008-11-28
I currently have dual boot but have not used windows for many months now). Ubuntu has served me well, and I want to reinstall for just single boot soon. I was thinking of installing linux mint instead of ubuntu since it has all the codecs etc and I thought it would be much easier (I have reinstalled ubuntu 3 times, and to be honest I am tired of the initial tweeking, including getting rid of the brown theme).

HOWEVER linux mint has the windows start button type of menu! I much prefer the logic of ubuntus menus (applications, places, system) which I am realising is far better than the windows approach (I have to use windows at work).

Is there a good alternative which won't involve me learning a different linux system, or can I change the mint menu (simply) to ubuntu style menu.

I'm writing this in the cafe cos its not urgent (just a reflection) and I'd be interested to hear any other tips or distros that they think would be perfect for an ubuntu like experience but without the set-up hassles?

---

### Post by eternalnewbee on 2008-11-28
> I was thinking of installing linux mint instead of ubuntu since it has all the codecs etc and I thought it would be much easier (I have reinstalled ubuntu 3 times, and to be honest I am tired of the initial tweeking, including getting rid of the brown theme).
> HOWEVER linux mint has the windows start button type of menu! I much prefer the logic of ubuntus menus (applications, places, system) which I am realising is far better than the windows approach (I have to use windows at work).

Try icon themes.
[www.gnomelook.org](www.gnomelook.org)

---

### Post by the yawner on 2008-11-28
> **uberdonkey5 said:**
> 
HOWEVER linux mint has the windows start button type of menu! I much prefer the logic of ubuntus menus (applications, places, system) which I am realising is far better than the windows approach (I have to use windows at work).

Is there a good alternative which won't involve me learning a different linux system, or can I change the mint menu (simply) to ubuntu style menu.


My only experience with Linux mint was back in their 7.04 version. But I do recall that like OpenSuse, they only replaced the Main Menu applet with the custom slab menu. You could replace it with the Menu Bar applet which is the default in Ubuntu. Unless they removed it on their recent versions but that's unlikely.

---

### Post by uberdonkey5 on 2008-11-28
I'm not too bothered about the appearance, as long as it isn't the standard ubuntu brown. I think I'll give mint a bash and just change the menu bar.

Thanks!

ud5

---

### Post by bruce89 on 2008-11-28
> **uberdonkey5 said:**
> I'm not too bothered about the appearance, as long as it isn't the standard ubuntu brown. I think I'll give mint a bash and just change the menu bar.

Switching distro based on not liking a theme is a bit extreme.

---

### Post by uberdonkey5 on 2008-11-28
> **bruce89 said:**
> Switching distro based on not liking a theme is a bit extreme.

yeh yeh! thats what I am trying to say. Theme isn't important, its just the menu bar and the codecs that I want (I spent alot of time tweaking ubuntu last time to get all the codecs and drivers I needed, and I want a distro thats quick to reinstall)

---

### Post by bruce89 on 2008-11-28
> **uberdonkey5 said:**
> yeh yeh! thats what I am trying to say. Theme isn't important, its just the menu bar and the codecs that I want (I spent alot of time tweaking ubuntu last time to get all the codecs and drivers I needed, and I want a distro thats quick to reinstall)

I don't understand the fuss about codecs, it's really just one command ```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by rudihawk on 2008-11-28
> **bruce89 said:**
> i don't understand the fuss about codecs, it's really just one command ```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
```

+1

---

### Post by Tom--d on 2008-11-28
And the menu can just be installed in Ubuntu.

Just download their .deb package here:

[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

---

### Post by burnetbj on 2008-11-28
Hi there

Another command to try out if that other doesnt work for ya is 

sudo apt-get install ubuntu-restricted-extras

---

### Post by bruce89 on 2008-11-28
> **burnetbj said:**
> sudo apt-get install ubuntu-restricted-extras

This installs a lot of useless stuff such as the non-free Java, the non-free Flash plugin, the Windows codec GStreamer thingy and the non-free unrar.

---

### Post by uberdonkey5 on 2008-11-28
> **burnetbj said:**
> Hi there

Another command to try out if that other doesnt work for ya is 

sudo apt-get install ubuntu-restricted-extras

yeh, thats what the fuss is about codecs. For some stuff you need more than the standard medibuntu codecs. Also, for recording to mp3 format you need to install additional stuff (sorry I have about a page of things I wrote down for all the different codecs).I was also worried about using my 3M modem that plugs into USB (that I use at home) but I hear intrepid comes with this already supported (it is regularly a pain and takes several attempts to connect properly, and this had to be installed on Hardy).

Its just I was wanting a clean install, and I can see its going to take at least a day (if it goes smoothly) to get the system the same as I have it now, based on my experience in Gutsy/Hardy.

---

### Post by bruce89 on 2008-11-28
> **uberdonkey5 said:**
> yeh, thats what the fuss is about codecs. For some stuff you need more than the standard medibuntu codecs. Also, for recording to mp3 format you need to install additional stuff (sorry I have about a page of things I wrote down for all the different codecs).I was also worried about using my 3M modem that plugs into USB (that I use at home) but I hear intrepid comes with this already supported (it is regularly a pain and takes several attempts to connect properly, and this had to be installed on Hardy).

None of the GStreamer plugins I suggest installing are from that repository. They are all in the main Ubuntu one. The only reason you'd need any other codecs is if you didn't use programs that use GStreamer.

---

### Post by blakjesus on 2008-11-28
> **bruce89 said:**
> This installs a lot of useless stuff such as the non-free Java, the non-free Flash plugin, the Windows codec GStreamer thingy and the non-free unrar.

I dont think those are useless. Around 50% of the websites i use have either flash or java embeded  into the page, and i run into .rar files alot on the internet. So it makes it really easy for me when i install a system for me or others.

---

### Post by bruce89 on 2008-11-28
> **blakjesus said:**
> I dont think those are useless. Around 50% of the websites i use have either flash or java embeded  into the page, and i run into .rar files alot on the internet. So it makes it really easy for me when i install a system for me or others.

I was thinking more along the lines of there being a Free Java, and Free Flash implementations. I don't care about rar, I never care for anything that is compressed with it (illegal stuff, ignorance).

---

