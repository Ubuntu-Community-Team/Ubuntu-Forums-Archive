---
title: "On vanilla 8.04, does YouTube prompt you for a plugin?"
date: 2008-04-29
forum: The Cafe
---

### Post by aysiu on 2008-04-29
Someone claimed through some experiment that visiting a YouTube video page takes you to the Adobe download page instead of the prompt to install the missing plugin using the package manager.

I tested it myself and found that YouTube does actually prompt you to install the missing plugin, just as any Flash page does.

Am I the only one? Was this person's installation for his girlfriend a fluke? Or did he just make it up so he could declare Linux not ready for the desktop?

If you've already installed and tweaked Ubuntu, you can test this by just using the live Ubuntu CD (or Desktop CD) and visiting a YouTube page.

---

### Post by Quillz on 2008-04-29
Yes, I'm prompted for a plug-in, and sometimes it works, sometimes it doesn't. It's just a gamble, unfortunately.

---

### Post by plun on 2008-04-29
Well... too lazy.

Can someone clarify if **Ubufox** is installed by default ?

[http://packages.ubuntu.com/hardy/ubufox](http://packages.ubuntu.com/hardy/ubufox)

This situation with commercial codecs is a disaster and also how involved
officials handle these challengies.  

The world ***_IS commercial_*** and this mess just kills Ubuntu and Linux.

I have never been so dissipointed as with Hardy and this mess.

There is one sticky thread in "**Multimedia and Video**" which is a "light in the tunnel", thanks for that !!!

Can someone also clarify how a newbie should know about ubuntu-restricted-extras   ???   a real scandal....

Software religion....  I hate it...:(

---

### Post by piousp on 2008-04-29
Plug-in for me

---

### Post by aysiu on 2008-04-29
> **Quillz said:**
> Yes, I'm prompted for a plug-in, and sometimes it works, sometimes it doesn't. It's just a gamble, unfortunately.
When you say it sometimes doesn't work, what exactly happens when it doesn't work?

---

### Post by aysiu on 2008-04-29
> **plun said:**
> 
Can someone clarify if **Ubufox** is installed by default ?

[http://packages.ubuntu.com/hardy/ubufox](http://packages.ubuntu.com/hardy/ubufox) Yes, it is:
[http://packages.ubuntu.com/hardy/ubuntu-desktop](http://packages.ubuntu.com/hardy/ubuntu-desktop)

> This situation with commercial codecs is a disaster and also how involved
officials handle these challengies. I don't really see how it's a disaster. Can you explain a bit more?  

> The world ***_IS commercial_*** and this mess just kills Ubuntu and Linux. It doesn't really kill Linux. There are plenty of Linux distros that have proprietary codecs preinstalled (Linux Mint, Linspire, PCLinuxOS, Mepis). I bought an Eee PC, which has Xandros preinstalled with all appropriate proprietary codecs working out of the box.

Ubuntu is not the same as Linux. Ubuntu is a subset of Linux.

> I have never been so dissipointed as with Hardy and this mess. Okay.

> There is one sticky thread in "**Multimedia and Video**" which is a "light in the tunnel", thanks for that !!!

Can someone also clarify how a newbie should know about ubuntu-restricted-extras   ???   a real scandal.... They're not supposed to. They're supposed to visit a site requiring Flash and be prompted to install Flash, or visit a site requiring Java and be prompted to install Java, or double-click an MP3 and be prompted to install MP3 playback.

> Software religion....  I hate it...:( Ubuntu has a philosophy and wants to stick with it. They have a right to. Sorry.
[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

If it bothers you that much, use something else, then. I mentioned a number of other Linux distros that include proprietary software by default.

---

### Post by agim on 2008-04-29
It has always brought me to the adobe page. I really didn't think much of it. I learned how to download flash from adobe. Then learned about flashplugin-nonfree. But it always takes me to adobe's page.

---

### Post by aysiu on 2008-04-29
Are the people being taken to the Adobe page using 64-bit Ubuntu or something? I'm trying to figure out what it is.

---

### Post by bobdob20 on 2008-04-29
I am using x64 and it promoted me to install the missing plug-in.

---

### Post by Lostincyberspace on 2008-04-29
Fire Fox prompts you to install the plugin not Youtube. Youtube will send you to the adobe page to download the yum, rpm or source.

---

### Post by Ozor Mox on 2008-04-29
If you ignore JavaScript-formed links that YouTube and other sites might give you, then yes Firefox will do the work for you. For me it appeared in the drop-down bar at the top, and I installed it no problem. It also gave me the choice of swfdec and Gnash.

---

### Post by aysiu on 2008-04-29
> **Lostincyberspace said:**
> Fire Fox prompts you to install the plugin not Youtube. Youtube will send you to the adobe page to download the yum, rpm or source.
So you mean that some people are clicking the link from within the YouTube page instead of clicking the *Install missing plugins* button that drops down?

---

### Post by sub2007 on 2008-04-29
I got a prompt to download via the yellow bar at the top (does Firefox call it an Information Bar?) and the install worked perfectly for me on both my user accounts. I do use Swiftweasel though so I don't know how it works on Firefox.

I am fully confident doing the tar.gz download as well if I had to. Adobe really could do with making a .deb download though, even though it's easy enough for me to do it (and Adobe give instructions) things like Opera have a nice thing where you click Ubuntu and it gives you the right version to download (which comes as a .deb). As that article said, she had no problem installing a .deb - she just clicked the nice big Install button.

---

### Post by Ozor Mox on 2008-04-29
> **aysiu said:**
> So you mean that some people are clicking the link from within the YouTube page instead of clicking the *Install missing plugins* button that drops down?

If someone does that they will run in to problems since it links to the Adobe site, which only provides tar.gz, rpm and yum formats (why no deb?) Still, this is the fault of YouTube and Adobe and not really much Ubuntu or Firefox can do over what is already done. I think the Firefox popup is a little more 'obvious' than the YouTube link.

---

### Post by conehead77 on 2008-04-29
> **bobdob20 said:**
> I am using x64 and it promoted me to install the missing plug-in.

same here

---

### Post by aysiu on 2008-04-29
> **Ozor Mox said:**
> If someone does that they will run in to problems since it links to the Adobe site, which only provides tar.gz, rpm and yum formats (why no deb?) Still, this is the fault of YouTube and Adobe and not really much Ubuntu or Firefox can do over what is already done. I think the Firefox popup is a little more 'obvious' than the YouTube link.
I can't really fault YouTube for linking to the Adobe site. After all, how are they supposed to know you have UbuFox installed? It's definitely Adobe's fault for not making a .deb file. The two standard package formats new desktop users will encounter are .deb and .rpm.

I've created a Brainstorm idea on this:
[Convince Adobe to host a .deb of flashplugin-nonfree on its website](http://brainstorm.ubuntu.com/idea/7844/)

I also went to Adobe's website and submitted it as a feature request.

---

### Post by agim on 2008-04-30
As always aysiu, thanks for being on top of things. I have followed some of your how-to posts and links to websites and such in the past. Just letting you know its appreciated.

---

