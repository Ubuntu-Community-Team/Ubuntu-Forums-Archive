---
title: "Questions about Virtualbox - XP host/ Gutsy Guest"
date: 2008-01-24
forum: Virtualisation
---

### Post by trishacupra on 2008-01-24
Hi,

I love Ubuntu, and really dislike Windows. I've been dual-booting XP and Gutsy (since Feisty was released) on my laptop.

I'm going to give a lot of details so you know my situation and if there's a better solution than what I want to do, you can steer me in a better direction.

Until recently, I mostly used Ubuntu rather than XP. Feisty ran very well on my laptop (Compaq Presario V2000 with 40GB hard drive, 896Mb RAM (1Gb shared with graphics card), Mobile AMD Sempron 3000+ processor - 1.79GHz, and crappy ATI Radeon Xpress 200M graphics card).

I'm a web designer primarily, and I do some graphic design as well, using Photoshop. (I don't have enough time to learn GIMP any time soon, though I wish I'd learned GIMP initially.) 

I even got Photoshop CS2 working somewhat on Ubuntu - though it was more for quick tasks because it doesn't work flawlessly. I'd have to power up XP if I had a big job to do in CS2 or I'd get too frustrated.

Ubuntu was great for my web designing. I now create sites driven by Wordpress (as it's an open source CMS), so I ditched Dreamweaver. So I just need Firefox to do that. What I really love about Ubuntu is Konqueror. Being able to use FTP in Konqueror and drag files from one server to another is fantastic, and using any XP FTP client is a real pain compared to how easy it is with Konqueror.

Everything changed, though, when I started this year-long trip travelling around Australia (started the trip 7 weeks ago). I couldn't live without an internet connection, as I'm still working part-time on the road, so I signed up with Virgin Mobile Broadband. I knew that the USB broadband modem that works on the 3G network (UMTS) is only supported on Windows and Mac machines, but I was desperate and this was the only affordable option for me.

For the life of me, I can't get this Globe Surfer Icon 7.2 modem to work in Ubuntu. It doesn't help that this is my ONLY available internet connection, so it's not like I can just apt-get something new to help me connect.

So, I've been reading about Virtualization. I've realised that in the beginning, as a complete newbie, I probably should have installed Ubuntu as a virtual machine rather than going dual-boot. Dual-booting is a real pain. 

And from what I've read, if I run Ubuntu as a guest in a Windows host, my internet connection in Windows should work in Ubuntu. That would mean I could finally start using Konqueror again for FTP. And I could use Firefox, Thunderbird, Open Office, etc, in Ubuntu rather than in Windows (which I do at the moment). Then I could just use Photoshop in XP.

Another thing that is a pain is that I have an external drive that I use a lot (as my laptop's hard drive is only 40Gb) but since I used Ubuntu every day, I made all my partitions Ext3 format. Now, using the Ext2IFS driver, my ext3 partitions on my laptop's hard drive show up reliably, but I have a lot of trouble with the external hard drive's partitions mounting reliably. So, I'd love to be able to get rid of that problem - even if I have to change everything to NTFS format, which I've never had trouble reading in Ubuntu.

I have Virtualbox installed in XP, ready to use. 

Now, I have some questions. 

1. Is using Ubuntu as a guest in XP really going to make it possible to use the internet in Ubuntu?

2. I've read stuff about USB devices not working. My mouse and my modem are both USB devices, and I use a USB card reader, an USB external hard-drive, an iPod, etc. Is this going to be an issue?

3. Is 896Mb RAM going to be enough memory? How much will Ubuntu need to work properly, using mainly Firefox (with a lot of tabs open), Thunderbird, and Open Office? I don't mind Photoshop in XP being a bit slow, because I don't use it every single day, and not for very intense stuff. I don't do video editing or anything like that.

4. If it's not enough memory, might it be worth adding more to my laptop? I don't have the skills to do it by myself, so I'd have to hire someone. I haven't gotten any quotes, but it sounds like it could get expensive. I know this is more of a 'personal opinion' question than a factual one, but I'm looking for opinions here.

5. How much disk space will I need to install Ubuntu using Virtualbox? Should I use the fixed or flexible disk space option? Does this space include that used by what will be my Home directory? I currently have three partitions on my 40Gb hard drive - Windows XP (NTFS), Ubuntu root (ext3), and Ubuntu Home (ext3). Which brings me to...

6. Will I be able to use my Home partition with Ubuntu installed using Virtualbox? If so, how do I set that up? If not, can I copy my home directory from the partition to the new home directory?

7. How does accessing and saving files work when using Ubuntu virtually? For example, if I want to edit a file that is in the /etc/ directory without running Ubuntu (so, I'd be in XP and editing it in Notepad), is that possible? Can I access my files in My Documents while in Ubuntu? When I save something in Ubuntu, can I save to another partition? Or is it saved in some kind of virtual file system I can't access unless I'm running Ubuntu in Virtualbox?

I have more questions, but they depend on the answers to these questions.

Please don't ask me to 'Just try it and see for yourself.' I'd normally do that, but all three of my partitions on my 40Gb internal hard drive are almost full, and I'd have to do a massive job of backing up and deleting my root partition and home partition to be able to expand my Windows partition (only a gig or two left on it - just enough for Windows to run with breathing room). 

I want to know if it's worthwhile first before possibly destroying my dual-boot setup.

Thanks in advance for any answers to my many questions.

---

### Post by theRightNee on 2008-01-24
LOL

i am sorry, but this post reminded me of all the pain i went through experimenting with virtualization. I will tell you all i can:
I prefer to use VMWare virtualization programs, simply because that is what I am most familiar with, and seems to be very well documented, I am sorry I cannot say much on virtualbox:
1. Yes-choose a NAT network connection (i suggest installing VMWare Server for ease of use)
2. If you are running it off of a Windows Host you should not run into many issues. As Windows has such a large hold on the software market, most software developed for Windows are less of a headache than those developed for Linux OS's
3. 896 is plenty-if i understand properly, the RAM you set is actually taken from the physical realm-not part of the hard disk, so the question you should be asking is if there is enough RAM left over for Windows
4. Adding RAM is proably going to more costly on a laptop-but if you are willing, pop the lid and see what is inside-however, Ubuntu is a very light operating system, 256 MB should be fine for web surfing and word processing (i do not know about photoshopping though)
5. Depending on what you will need-do not make it too small, because ,apparently, when Linux runs out of space, things turn nasty; however 8-10 GB should be fine, especially if you're not saving files to the Linux space
6. if you are referring to the Ubuntu home partition, my answer would have to be no, because i do believe it is not recognized by Windows, and if it is not recognized you will not be able to access it 
         my advice (if you have time and some patience) would be to download a copy of GParted, erase your Ubuntu related extensions to make space for your virtualized version
7. Yes you can please refer to this tutorial 
     CLICK HERE!!![http://www.lifehack.org/articles/technology/beginners-guide-run-linux-like-any-other-program-in-windows.html]("http://www.lifehack.org/articles/technology/beginners-guide-run-linux-like-any-other-program-in-windows.html")
 
Please Note: This only allows sharing for that folder, and you cannot access folders on your Virtual Linux (its proabably written in a way that cannot be read anyway); best to save all your files to a shared folder

Here is all you asked for, please feel free to ask more:

My advice:
   If you have some time off (preferably a day or two), the urge to do something crazy, a 2+ GB flash drive..do a clean install of Ubuntu, erasing everything.
       BEFORE YOU DO THAT:
          Download the Linux version of vmware server/vmware player and a windows xp OS (if you do not have one handy)
          Move it to your flash drive
  Then Install
After installing, setup your virtual XP...then set up a Bridged network (this is because only your Windows machine will be able to access the internet)

This is only if you truly feel adventurous, please note that.
I recommend this because:
It allows great system stability-(no spyware, no adware, no worms, no trojans that will reach the heart of your systeml;just the virtual files)
Ubuntu is a rather light OS, so more system resources can be used efficiently (rather than being wasted with Windows)
With a Ubuntu host and a Windows Guest you can have 3D acceleration (cannot seem to work the other way...been there tried that)
The eye-candy goodness of Compiz fusion-and its free!
And Ubuntu is just 100% awesomeness...


i hope this helps, and please do not erase everything until you have plenty of time to take care of your mistakes (and nothing due anytime soon) =]
Best of Luck

---

### Post by theRightNee on 2008-01-24
i stumbled upon this in my surfing, and found it very intriguing, perhaps you may be interested as well 

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by trishacupra on 2008-01-24
Thanks for your answers. That does look interesting.

I really need to use Windows as the host, though, or I can't connect to the internet.

---

### Post by theRightNee on 2008-01-25
i understand, i also ran into many issues with my wireless adapter with a Ubuntu host, hopes all goes well!

---

