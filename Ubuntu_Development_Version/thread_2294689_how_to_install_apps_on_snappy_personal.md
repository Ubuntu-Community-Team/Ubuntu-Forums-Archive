---
title: "how to install apps on snappy personal"
date: 2015-09-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-09-12
Just got some info back in on this which was a show stopper - so there might be some fun after all :)

> 
                                                                              [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG][IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]                


                        
                          
                        On 09/11/2015 10:00 PM, ventrical wrote:
> Seems that webdm will not install.
> 
> webdm failed to install:snappy package not found
 
Ah, I forgot about that-- you have to sideload it since they haven't
released it in the Personal channel yet. Directions in the description
of the MP here:
 
[https://code.launchpad.net/~kyrofa/ubuntu-seeds/ubuntu-touch.wily_add_unity-scope-snappy/+merge/265568]("https://code.launchpad.net/%7Ekyrofa/ubuntu-seeds/ubuntu-touch.wily_add_unity-scope-snappy/+merge/265568")
 
--
Kyle Fazzari (kyrofa)
Software Engineer
Canonical Ltd.



---

### Post by ventrical on 2015-09-12
I am not able to get this to work. I assume as the dev refers to 'sideload' that he is talking about tablets and phones. I tired to enter the command into snappy terminal and says I need to install

```

sudo apt-get install curl
{/CODE]

which of course will not work on snappy

but the command 

[CODE]
wget `curl [http://search.apps.ubuntu.com/api/v1/package/webdm](http://search.apps.ubuntu.com/api/v1/package/webdm) | perl -pe 's/.*"anon_download_url":\s*"(.*?)",.*/\1/'`

```
works just fine on gnome-terminal. 

I tired to configure to move the file package over to snappy /home/ but it keeps bouncing back , even with root.

Regards..

---

### Post by grahammechanical on 2015-09-12
I have heard the term "sideload" used in a blog somewhere. So, I looked it up in wikipedia. It seems to mean installing the app on a mobile device over a connection to a local computer. Similar to transferring audio files from computer to smart phone.

[https://en.wikipedia.org/wiki/Sideloading](https://en.wikipedia.org/wiki/Sideloading)

Sideloading seems to be used by the devs to get apps on their Ubuntu phone reference devices that are not in the app store.

EDIT: This is proving hard to find. There has been recently released something Snapcraft. That makes it easy to build a snap and it is done on a desktop/laptop machine. I imagine that sideloading would used to test the snap on a device before the app is pushed into the app store. But I have still to find how to sideload from Ubuntu. Unless we use adb.

[https://developer.ubuntu.com/en/snappy/snapcraft/your-first-snap/](https://developer.ubuntu.com/en/snappy/snapcraft/your-first-snap/)

[https://wiki.cyanogenmod.org/w/Doc:_adb_intro](https://wiki.cyanogenmod.org/w/Doc:_adb_intro)

---

### Post by ventrical on 2015-09-12
I had worked extensively  attempting to restore an ARM ubuntu-image using the sideload technique to an RCA Voyager 7" tablet(s) with only absolute fails. (Not sure how Cariboo made out with his.) Problem is it has to be rooted and the free rooting programs out in the wild are suspect. Speaking for myself only I could not root those devices and the sideload (ing) options kept failing - otherwise I would be testing snappy-personal on the ARM architecture. (There was some  sort of lock with Fastboot:)

I had also assumed that Kyle was speaking of this (sideloading to tablets) because in his video he is using a Raspberry Pi device which is sideloaded to his laptop . I will leave him another e-mail and describe that this process does not seem to work on desktop/hdd technique.  I have a whole install devoted to sideload and have studied it  best as I could ... the end resultant problem is that the devices that are supported are above and beyond my current budget for beta testing. I'll keep working with what I have and all support and suggestions  is welcome and will probably lead to a resolve of this issue.

regards..

---

### Post by ventrical on 2015-09-12
Here is snappy personal sideloading IoT

[https://rainveiltech.com/posts/snappy-scope-progress-update](https://rainveiltech.com/posts/snappy-scope-progress-update)

---

### Post by QDR06VV9 on 2015-09-13
Added Info
> What is sideloading?  It's a term you see a lot thrown around while talking about Android applications, and it's simple to explain.  It means installing applications without using the official Android Market.  What's less simple is how it's done and why you would do it.  That's where this post comes in.  Let's explain it, shall we?

How to do it is easy enough, so let's start there.  In the Application settings on your Android phone, you'll find a check box to "Allow installation of non-Market applications."  When it's checked, you can sideload.  You'll also see a pop-up warning when you check this box letting you know that your phone is now more vulnerable to attacks from applications, and that you accept all the responsibility that comes with doing this.  It makes sense -- you can't hold Google responsible for applications you didn't download through their service using their security methods.  
I have the need from time to time to sideload APKs testing Android.
Hope this dose not become common behavior. (For Snappy)

---

### Post by grahammechanical on 2015-09-13
Ubuntu Personal on USB stick.

I just tried to install webDm (snappy install webdm) result = package not found. So, what repositories is Personal accessing? This install at the moment is booting system-a image. So, on the desktop I go to etc/apt/sources.list of the system-a partition and it has a very limited set of software sources.

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily-security universe




Double clicking sources.list will open a dialog where you can add resources. As the file system is read only I expect it will need naultilus running as root in order to change anything. But what repository to add to get the snaps in the snap store? I would not be surprised if any changes get over-written by the next system image transactional update.

---

### Post by ventrical on 2015-09-13
> **grahammechanical said:**
> Ubuntu Personal on USB stick.

<...



Double clicking sources.list will open a dialog where you can add resources. As the file system is read only I expect it will need naultilus running as root in order to change anything.  ...>

Tried that. I left a link with instructions how to sideload the webdm app. I tired to slip it in  via root and it just keeps bouncing back. Left details of this with kyle-dev.

I am beggining to understand that we are dealing with two different  frameworks here . Snappy-core and snappy-personal.  Snappy-core can have webdm installed on it. Snappy-personal is fixed. Unless we are using a tablet or smart phone I think we will just have to wait for oli and Sebastian Bacher to keep sending new versions of the image up.. but I'll keep working at it as I know the rest of you will also :)



Regards..

---

### Post by ventrical on 2015-09-14
@graham,ruckus

Here is latest helper from dev engineer. I have a big job today so I will be working all day.

Thanks..

> 
                                      
                          
                        Hey Dale,
 
On 09/12/2015 07:49 PM, Dale Beaudoin wrote:
> Hi kyle
> 
> Thanks for your reply. Thing is I am running the personal_x86.img on an
> hdd on a larger desktop. I have is so the image boots right off of
> system-b. I tried to download in snappy cli but it tells me I need curl
> which is >sudo-apt-get curl> which does not work on snappy.
> 
> I next downloaded it (the webdm fix) on a gnome terminal in another
> install of regular ubuntu and then tried to put the pacjage into the
> home directory on system-b but it is hard set for root user and I cannot
> drag the webdm package to the /home/ on the snappy system-b.
 
Heh-- Ah, alpha systems, eh?
 
Okay, assuming I understand your issue correctly, you can use a manual,
less-cool version of the description in that MP that uses curl and stuff.
 
Manually download this, either with wget on snappy or on your normal
Ubuntu install:
 
[http://search.apps.ubuntu.com/api/v1/package/webdm](http://search.apps.ubuntu.com/api/v1/package/webdm)
 
Open it up, and you'll find just it's just a JSON file. Look through
there for the "anon_download_url" and that's the WebDM snap you need to
download. You find this URL:
 
[https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap](https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap)
 
Copy it and download it on the Snappy install via wget, i.e.
 
$ wget
[https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap](https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap)
 
And install it with:
 
$ snappy install webdm.canonical_0.9_multi.snap
 
Does that work?
 
--
Kyle Fazzari (kyrofa)
Software Engineer
Canonical Ltd.
[EMAIL="kyle@canonical.com"]kyle@canonical.com[/EMAIL]

---

### Post by QDR06VV9 on 2015-09-14
> [COLOR=#000000]I am beggining to understand that we are dealing with two different frameworks here . Snappy-core and snappy-personal. Snappy-core can have webdm installed on it. Snappy-personal is fixed. [/COLOR]
That was my guess Also
I will go with snappy core today,  Thanks also for the updated info.
Regards

---

### Post by grahammechanical on 2015-09-14
The full URL is

[https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap](https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap)

It is truncated by the forum tags. The missing section is

> anon/download/canonical/webdm.canonical/wedbm.canonical_0.9_multi.snap

On snappy personal in tty1 I ran

```
sudo wget https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap
```

and in the printout there is this:

> connected http request sent awaiting response 401 UNAUTHORISED username/password failed

There is no point in running the install command = package not found.

I did not login to the desktop. I went straight to tty1. Was that something to do with it? Or is it expecting a connection with SSO?

Regards.

---

### Post by QDR06VV9 on 2015-09-14
@grahm I am at a loss here also.
In the video that vent had provided yesterday, I noticed he was sideloading using URLs.
And vent also pointed out maybe 2 different frameworks.
I duno? I am going to install core today, and will post back anything useful.
Regards
Edit: Found a little more info for the Difference's
> Please note that Snappy and Ubuntu Core are different. Snappy is a new technology implemented in the Ubuntu Core, whereas Ubuntu Core is a minimal rootfs for use in the creation of custom images for specific needs. Ubuntu Core strives to create a suitable minimal environment for use in Board Support Packages, constrained or integrated environments, as the basis for application demonstration images, or Linux containers such as LXC or Docker.
From Here [http://www.unixmen.com/snappy-ubuntu-core-an-entirely-new-ubuntu-operating-system-for-clouds-and-devices/](http://www.unixmen.com/snappy-ubuntu-core-an-entirely-new-ubuntu-operating-system-for-clouds-and-devices/)
Edit: I give up. To frustrated to even continue.
Leaving it to you and grahm.(I'm taking my ball and going home:p)
Have fun.:D

---

### Post by ventrical on 2015-09-14
> **grahammechanical said:**
> The full URL is

[https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap](https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap)

It is truncated by the forum tags. The missing section is



On snappy personal in tty1 I ran

```
sudo wget https://public.apps.ubuntu.com/anon/download/canonical/webdm.canonical/webdm.canonical_0.9_multi.snap
```



 I did exactly the same as you except that I did not use (sudo). I started right off with wget and my printout is this:

Length ->
Saving to ->
webdm.canonical_0.9_multi.snap 100%:[---------------] 6.16M in 14.s etc..


remember.. when you log in on tty1 with  <ubuntu> <ubuntu> you are in root - so sudo not needed in this case ( I assume)  . but <sudo> is needed  when using the 'install' command.

Regards..

---

### Post by ventrical on 2015-09-14
..and ..

```

$sudo snappy install webdm.canonical_0.9_multi.snap

```

and it installed! :)

```


Installing webdm.canonical_0.9_multi.snap

```


Regards..

---

### Post by ventrical on 2015-09-14
Report:

Even though I was able to install webdm, then:

```

sudo snappy update

```

and it updated to (92) ... the apps store still does not work.

.. and so this is a work in progress .. a *highly experimental* development slice. Some things we do will break the install. That may be inconvenient but it gives early adopters, perhaps, a better perspective on what to expect to come down the pipe in upcoming development.

I think it is good to havetwo installs of snappy-personal. One for testing and one to play it safe and just wait for updates.

note: btw .. after I had updated snappy it booted from 

```

system-a

```

Regards..

---

### Post by grahammechanical on 2015-09-14
I just tried again with no improvement. It connects to public.apps.ubuntu.com but then comes back with 401 UNAUTHORISED Username/Password Authentication Failed.

Have you tried using Firefox on a desktop install to log in to webdm? And then installing some snaps from snap store.

```
firefox http://webdm.local:4200
```

I do not think it will work. I think the developers are running stuff like this in a KVM. 

The roll back is achieved by having 2 system images - system-a & system-b. Editing configuration files would be useless if the config file in one system image was edited and not the other. An update to the system may not over-write an edited configuration file because transactional updates are only supposed to bring in the differences in code between what is installed and what is upgraded. It does not do it package by package.

What I am keeping in mind is that at present we have snappy ubuntu core running on x86 hardware and using Mir and Unity8 and it is wily code at that. I see that as a big step for Ubuntu kind. 

Regards.

---

### Post by ventrical on 2015-09-15
> **grahammechanical said:**
> I just tried again with no improvement. It connects to public.apps.ubuntu.com but then comes back with 401 UNAUTHORISED Username/Password Authentication Failed.

Have you tried using Firefox on a desktop install to log in to webdm? And then installing some snaps from snap store.

```
firefox http://webdm.local:4200
```



I will try that. Thanks for sending that up. I knew I was missing something in between the lines.:)

> 

I do not think it will work. I think the developers are running stuff like this in a KVM. 

The roll back is achieved by having 2 system images - system-a & system-b. Editing configuration files would be useless if the config file in one system image was edited and not the other. An update to the system may not over-write an edited configuration file because transactional updates are only supposed to bring in the differences in code between what is installed and what is upgraded. It does not do it package by package.

What I am keeping in mind is that at present we have snappy ubuntu core running on x86 hardware and using Mir and Unity8 and it is wily code at that. I see that as a big step for Ubuntu kind. 

Regards.

 Obviously Canonical is very  committed to this project. I think  they will be able to develop an automation process that will convert a lot of conventional .debs to snappy oriented code and we may be able to install apps and programs that we know and are used to. Also , certainly if one is into razors' edge testing, then this is the project that is offering a variety of modules that can be tested in several different ways. So there is  opportunity for discovery here if you have some programming background. I am keeping in mind that the core change here is the repository infrastructure an that ubuntu_linux itself is not being changed so there may be some room for mode changing in the core where an end_user can run conventional .debs that will not affect the system-a or system-b or system final. It will probably develop in a sense to system_snappy and system_ubuntu and one can mode switch either virtually, run consecutively  and/or concurrently.

Regards..

---

### Post by ventrical on 2015-09-15
More suited for Beaglebone Black. It keeps reporting  <Install firefox with apt-get> then <Cannot use apt-get in snappy core - see snappy --help .. etc.

regards..

---

### Post by ventrical on 2015-09-15
> **runrickus said:**
> @grahm I am at a loss here also.
In the video that vent had provided yesterday, I noticed he was sideloading using URLs.
And vent also pointed out maybe 2 different frameworks.
I duno? I am going to install core today, and will post back anything useful.
Regards
Edit: Found a little more info for the Difference's

From Here [http://www.unixmen.com/snappy-ubuntu-core-an-entirely-new-ubuntu-operating-system-for-clouds-and-devices/](http://www.unixmen.com/snappy-ubuntu-core-an-entirely-new-ubuntu-operating-system-for-clouds-and-devices/)
Edit: I give up. To frustrated to even continue.
Leaving it to you and grahm.(I'm taking my ball and going home:p)
Have fun.:D

Thanks for that link. Yeah .. it's like a spaggetti western for sure... the good , the bad and the unworkable .. :)

regards..

---

### Post by QDR06VV9 on 2015-09-15
> [COLOR=#000000] the good , the bad and the unworkable .. [/COLOR]:smile:
No further words needed.:oops:

---

### Post by ventrical on 2015-09-16
Lots of action here. I am able to open the Snap Drawer and use a lot of the pre-installed apps. One of those is reddit. It has pics and previews of games. It will call the browser. Not all of those advertised will play. In some instances it will ask you to install Google-Play app (which is not installed) so it will not work - however some of the games and animations Do work and they are just awesome. 

Another app that works is open library and it will allow you to read a lot of online books. It also calls the browser for this. Of course the weather channel app also works.

---

### Post by ventrical on 2015-09-16
I'll have to declare that one of my snappy-personal install to hdd and updated to (94) has broken. It will not install the new kernel and claims that there is not enough space on the disk. I have another install on USB and will work on that one until I can figure out what went wrong. Breakage expected of course in this *highly experimental* testing. I was able to get a good taste of where snappy-desktop-personal is going and it looks very promising with speed and better graphics but it looks like the run will come after the release of 15.10 and into 16.04.

Regards..

---

### Post by QDR06VV9 on 2015-09-16
Ventrical what link are using for your installs?
Cant seem to find it for snappy personal.
I have been using vagrant for snappy core.
Thanks
Edit: if this it [https://lists.ubuntu.com/mailman/listinfo/snappy-devel](https://lists.ubuntu.com/mailman/listinfo/snappy-devel)
Then never mind.
Regards
Edit:
> In case someone wants to test the functionality, you can now just build
an image from 15.04 with the --channel=edge option.

---

### Post by ventrical on 2015-09-16
> **runrickus said:**
> Ventrical what link are using for your installs?
Cant seem to find it for snappy personal.
I have been using vagrant for snappy core.
Thanks
Edit: if this it [https://lists.ubuntu.com/mailman/listinfo/snappy-devel](https://lists.ubuntu.com/mailman/listinfo/snappy-devel)
Then never mind.
Regards
Edit:

@runrickus

Open terminal and run the first command line (forget second unless you have qemu loaded)

You will find  <personal_x86.img> in your /home/ directory after you run the first command line.
 Use either 'disks' <restore image> to USB device or you can use mkusb 10.0.6 unstable.

> 
I am assuming that we can still get the new updated images by:

   ```

     sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode 
```
and then , if preferred..
     ```

     kvm -m 2048 -vga qxl personal_x86.img
```


---

### Post by QDR06VV9 on 2015-09-16
So will a vagrant file work that i already have? 
I had A .VDI that would make me pull all my hair out.
I will just follow what you have instructed me to do.
I am using [COLOR=#000000] mkusb 10.1.1 unstable[/COLOR]
Thank You Sir
Ok Having some fun now

---

### Post by ventrical on 2015-09-16
> **runrickus said:**
> So will a vagrant file work that i already have? 
I had A .VDI that would make me pull all my hair out.
I will just follow what you have instructed me to do.
I am using [COLOR=#000000] mkusb 10.1.1 unstable[/COLOR]
Thank You Sir
Ok Having some fun now

When you boot up  your USB after the personal_x86.img is restored to it you will get the Arrow of Mir at top left hand corner. *WAIT* and you will get the unity8 greeter and then log on with:

user_name> ubuntu

password>ubuntu

To get to terminal use:

Ctrl+Alt+F1 and then logon  in same manner.


I think vagrant stuff will only run on snappy core and you have to have cloud and other coniption  stuff in there. :)

It's one of those 'the further aheader I get, the farther behinder I are' kind of things atm.

Regards

---

### Post by QDR06VV9 on 2015-09-16
> **ventrical said:**
> 
I think vagrant stuff will only run on snappy core and you have to have cloud and other coniption  stuff in there. :)

It's one of those 'the further aheader I get, the farther behinder I are' kind of things atm.

Regards
Amen to that my friend:D
Your first command resulted with 
```
me@me-Aspire-M3300:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode[sudo] password for me: 
DEPRECATED: Implicit 'touch' subcommand assumed
unknown flag `o'
me@me-Aspire-M3300:~$ 

```
So i went with 
```
wget http://releases.ubuntu.com/15.04/ubuntu-15.04-snappy-amd64-generic.img.xz
```
Has to be a newer image out there.
Regards

---

### Post by ventrical on 2015-09-16
> **runrickus said:**
> Amen to that my friend:D
Your first command resulted with 
```
me@me-Aspire-M3300:~$ sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode[sudo] password for me: 
DEPRECATED: Implicit 'touch' subcommand assumed
unknown flag `o'
me@me-Aspire-M3300:~$ 

```
So i went with 
```
wget http://releases.ubuntu.com/15.04/ubuntu-15.04-snappy-amd64-generic.img.xz
```
Has to be a newer image out there.
Regards

You have to install the ubuntu-device-flash thingy in there. lemme look back..

---

### Post by ventrical on 2015-09-16
@runrickus

```

sudo apt-get install ubuntu-device-flash

```

then run that first line of code.

:) 

regards..

---

### Post by ventrical on 2015-09-16
Good step by step study of what we did here: [http://ubuntuforums.org/showthread.php?t=2286066&p=13318005#post13318005](http://ubuntuforums.org/showthread.php?t=2286066&p=13318005#post13318005)

---

### Post by QDR06VV9 on 2015-09-16
I Do
```
apt-cache policy ubuntu-device-flashubuntu-device-flash:
  Installed: 0.19-0~142~ubuntu14.04.1
  Candidate: 0.19-0~142~ubuntu14.04.1
  Version table:
 *** 0.19-0~142~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.16-0ubuntu1 0
        500 http://ppa.launchpad.net/phablet-team/tools/ubuntu/ trusty/main amd64 Packages
     0.2+14.04.20140416.2-0ubuntu1 0
        500 http://mirror.internode.on.net/pub/ubuntu/ubuntu/ trusty/universe amd64 Packages



```

---

### Post by ventrical on 2015-09-16
> **runrickus said:**
> I Do
```
apt-cache policy ubuntu-device-flashubuntu-device-flash:
  Installed: 0.19-0~142~ubuntu14.04.1
  Candidate: 0.19-0~142~ubuntu14.04.1
  Version table:
 *** 0.19-0~142~ubuntu14.04.1 0
        500 http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.16-0ubuntu1 0
        500 http://ppa.launchpad.net/phablet-team/tools/ubuntu/ trusty/main amd64 Packages
     0.2+14.04.20140416.2-0ubuntu1 0
        500 http://mirror.internode.on.net/pub/ubuntu/ubuntu/ trusty/universe amd64 Packages



```

Whoops ..... I forgot to specify that it is recommended that you use the wily repos from a wily install. Mayby it will work with what you have.

regards..

---

### Post by QDR06VV9 on 2015-09-16
This is what I get if I change to wily
```
 Err http://ppa.launchpad.net wily/main Sources                                   404  Not Found
Err http://ppa.launchpad.net wily/main amd64 Packages                          
  404  Not Found
Err http://ppa.launchpad.net wily/main i386 Packages                           
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_US                       
Ign http://ppa.launchpad.net wily/main Translation-en                          
Fetched 1,109 kB in 37s (29.8 kB/s)                                            
W: Failed to fetch http://ppa.launchpad.net/phablet-team/tools/ubuntu/dists/wily/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/phablet-team/tools/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/phablet-team/tools/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found


 
```

---

### Post by ventrical on 2015-09-16
I don't remember a ppa... I'll be back in a few..

Enable Canonical Partners repo

no ppas needed

Regards..

---

### Post by QDR06VV9 on 2015-09-16
> **ventrical said:**
> I don't remember a ppa... I'll be back in a few..
OMG Homer Simpson moment here thought i was on wily but i fired Trusty up](*,)
Porch Light's on and nobody Home. Dooh!
No PPA needed for Wily.
Sheesh
Any way now I'm getting it as we speak.
Thanks vent

---

### Post by ventrical on 2015-09-16
Good stuff... here is what it should look like:

```

ventrical@ventrical-MS-7850:~$ sudo apt-get install ubuntu-device-flash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cpp-4.9 libboost-filesystem1.55.0 libboost-system1.55.0 libcloog-isl4
  lubuntu-artwork-15-04ventrical@ventrical-MS-7850:~$ sudo apt-get install ubuntu-device-flash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cpp-4.9 libboost-filesystem1.55.0 libboost-system1.55.0 libcloog-isl4
  lubuntu-artwork-15-04
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-snappy-cli
Suggested packages:
  debian-keyring
The following NEW packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-device-flash ubuntu-snappy-cli
0 upgraded, 12 newly installed, 0 to remove and 252 not upgraded.
Need to get 9,050 kB/10.9 MB of archives.
After this operation, 98.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily/universe qemu-user-static amd64 1:2.3+dfsg-5ubuntu5 [7,248 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily/main kpartx amd64 0.5.0-7ubuntu4 [23.3 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily/universe ubuntu-device-flash amd64 0.30-0ubuntu1 [1,778 kB]
Fetched 9,050 kB in 21s (418 kB/s)                                             
Selecting previously unselected package binfmt-support.
(Reading database ... 138325 files and directories currently installed.)
Preparing to unpack .../binfmt-support_2.1.5-1_amd64.deb ...
Unpacking binfmt-support (2.1.5-1) ...
Selecting previously unselected package libxmltok1.
Preparing to unpack .../libxmltok1_1.2-3build3_amd64.deb ...
Unpacking libxmltok1 (1.2-3build3) ...
Selecting previously unselected package debsig-verify.
Preparing to unpack .../debsig-verify_0.13_amd64.deb ...
Unpacking debsig-verify (0.13) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.20.2-1ubuntu1) ...
Selecting previously unselected package qemu-user-static.
Preparing to unpack .../qemu-user-static_1%3a2.3+dfsg-5ubuntu5_amd64.deb ...
Unpacking qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Selecting previously unselected package android-tools-adb.
Preparing to unpack .../android-tools-adb_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package android-tools-fastboot.
Preparing to unpack .../android-tools-fastboot_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package click-ubuntu-policy.
Preparing to unpack .../click-ubuntu-policy_0.1_all.deb ...
Unpacking click-ubuntu-policy (0.1) ...
Selecting previously unselected package kpartx.
Preparing to unpack .../kpartx_0.5.0-7ubuntu4_amd64.deb ...
Unpacking kpartx (0.5.0-7ubuntu4) ...
Selecting previously unselected package ubuntu-snappy-cli.
Preparing to unpack .../ubuntu-snappy-cli_1.5ubuntu1_amd64.deb ...
Unpacking ubuntu-snappy-cli (1.5ubuntu1) ...
Selecting previously unselected package ubuntu-device-flash.
Preparing to unpack .../ubuntu-device-flash_0.30-0ubuntu1_amd64.deb ...
Unpacking ubuntu-device-flash (0.30-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for man-db (2.7.2-1) ...
Setting up binfmt-support (2.1.5-1) ...
Setting up libxmltok1 (1.2-3build3) ...
Setting up debsig-verify (0.13) ...
Setting up libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Setting up fakeroot (1.20.2-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Setting up android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Setting up android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Setting up click-ubuntu-policy (0.1) ...
Setting up kpartx (0.5.0-7ubuntu4) ...
Setting up ubuntu-snappy-cli (1.5ubuntu1) ...
Warning: The home directory /nonexistent you specified can not be accessed: No such file or directory
Adding system user `snappypkg' (UID 111) ...
Adding new group `snappypkg' (GID 124) ...
Adding new user `snappypkg' (UID 111) with group `snappypkg' ...
Not creating home directory `/nonexistent'.
Setting up ubuntu-device-flash (0.30-0ubuntu1) ...ventrical@ventrical-MS-7850:~$ sudo apt-get install ubuntu-device-flash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cpp-4.9 libboost-filesystem1.55.0 libboost-system1.55.0 libcloog-isl4
  lubuntu-artwork-15-04
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-snappy-cli
Suggested packages:
  debian-keyring
The following NEW packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-device-flash ubuntu-snappy-cli
0 upgraded, 12 newly installed, 0 to remove and 252 not upgraded.
Need to get 9,050 kB/10.9 MB of archives.
After this operation, 98.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily/universe qemu-user-static amd64 1:2.3+dfsg-5ubuntu5 [7,248 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily/main kpartx amd64 0.5.0-7ubuntu4 [23.3 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily/universe ubuntu-device-flash amd64 0.30-0ubuntu1 [1,778 kB]
Fetched 9,050 kB in 21s (418 kB/s)                                             
Selecting previously unselected package binfmt-support.
(Reading database ... 138325 files and directories currently installed.)
Preparing to unpack .../binfmt-support_2.1.5-1_amd64.deb ...
Unpacking binfmt-support (2.1.5-1) ...
Selecting previously unselected package libxmltok1.
Preparing to unpack .../libxmltok1_1.2-3build3_amd64.deb ...
Unpacking libxmltok1 (1.2-3build3) ...
Selecting previously unselected package debsig-verify.
Preparing to unpack .../debsig-verify_0.13_amd64.deb ...
Unpacking debsig-verify (0.13) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.20.2-1ubuntu1) ...
Selecting previously unselected package qemu-user-static.
Preparing to unpack .../qemu-user-static_1%3a2.3+dfsg-5ubuntu5_amd64.deb ...
Unpacking qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Selecting previously unselected package android-tools-adb.
Preparing to unpack .../android-tools-adb_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package android-tools-fastboot.
Preparing to unpack .../android-tools-fastboot_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package click-ubuntu-policy.
Preparing to unpack .../click-ubuntu-policy_0.1_all.deb ...
Unpacking click-ubuntu-policy (0.1) ...
Selecting previously unselected package kpartx.
Preparing to unpack .../kpartx_0.5.0-7ubuntu4_amd64.deb ...
Unpacking kpartx (0.5.0-7ubuntu4) ...
Selecting previously unselected package ubuntu-snappy-cli.
Preparing to unpack .../ubuntu-snappy-cli_1.5ubuntu1_amd64.deb ...
Unpacking ubuntu-snappy-cli (1.5ubuntu1) ...
Selecting previously unselected package ubuntu-device-flash.
Preparing to unpack .../ubuntu-device-flash_0.30-0ubuntu1_amd64.deb ...
Unpacking ubuntu-device-flash (0.30-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for man-db (2.7.2-1) ...
Setting up binfmt-support (2.1.5-1) ...
Setting up libxmltok1 (1.2-3build3) ...
Setting up debsig-verify (0.13) ...
Setting up libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Setting up fakeroot (1.20.2-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Setting up android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Setting up android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Setting up click-ubuntu-policy (0.1) ...
Setting up kpartx (0.5.0-7ubuntu4) ...
Setting up ubuntu-snappy-cli (1.5ubuntu1) ...
Warning: The home directory /nonexistent you specified can not be accessed: No such file or directory
Adding system user `snappypkg' (UID 111) ...
Adding new group `snappypkg' (GID 124) ...
Adding new user `snappypkg' (UID 111) with group `snappypkg' ...
Not creating home directory `/nonexistent'.
Setting up ubuntu-device-flash (0.30-0ubuntu1) ...ventrical@ventrical-MS-7850:~$ sudo apt-get install ubuntu-device-flash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cpp-4.9 libboost-filesystem1.55.0 libboost-system1.55.0 libcloog-isl4
  lubuntu-artwork-15-04
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-snappy-cli
Suggested packages:
  debian-keyring
The following NEW packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-device-flash ubuntu-snappy-cli
0 upgraded, 12 newly installed, 0 to remove and 252 not upgraded.
Need to get 9,050 kB/10.9 MB of archives.
After this operation, 98.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ wily/universe qemu-user-static amd64 1:2.3+dfsg-5ubuntu5 [7,248 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ wily/main kpartx amd64 0.5.0-7ubuntu4 [23.3 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ wily/universe ubuntu-device-flash amd64 0.30-0ubuntu1 [1,778 kB]
Fetched 9,050 kB in 21s (418 kB/s)                                             
Selecting previously unselected package binfmt-support.
(Reading database ... 138325 files and directories currently installed.)
Preparing to unpack .../binfmt-support_2.1.5-1_amd64.deb ...
Unpacking binfmt-support (2.1.5-1) ...
Selecting previously unselected package libxmltok1.
Preparing to unpack .../libxmltok1_1.2-3build3_amd64.deb ...
Unpacking libxmltok1 (1.2-3build3) ...
Selecting previously unselected package debsig-verify.
Preparing to unpack .../debsig-verify_0.13_amd64.deb ...
Unpacking debsig-verify (0.13) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.20.2-1ubuntu1) ...
Selecting previously unselected package qemu-user-static.
Preparing to unpack .../qemu-user-static_1%3a2.3+dfsg-5ubuntu5_amd64.deb ...
Unpacking qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Selecting previously unselected package android-tools-adb.
Preparing to unpack .../android-tools-adb_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package android-tools-fastboot.
Preparing to unpack .../android-tools-fastboot_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package click-ubuntu-policy.
Preparing to unpack .../click-ubuntu-policy_0.1_all.deb ...
Unpacking click-ubuntu-policy (0.1) ...
Selecting previously unselected package kpartx.
Preparing to unpack .../kpartx_0.5.0-7ubuntu4_amd64.deb ...
Unpacking kpartx (0.5.0-7ubuntu4) ...
Selecting previously unselected package ubuntu-snappy-cli.
Preparing to unpack .../ubuntu-snappy-cli_1.5ubuntu1_amd64.deb ...
Unpacking ubuntu-snappy-cli (1.5ubuntu1) ...
Selecting previously unselected package ubuntu-device-flash.
Preparing to unpack .../ubuntu-device-flash_0.30-0ubuntu1_amd64.deb ...
Unpacking ubuntu-device-flash (0.30-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for man-db (2.7.2-1) ...
Setting up binfmt-support (2.1.5-1) ...
Setting up libxmltok1 (1.2-3build3) ...
Setting up debsig-verify (0.13) ...
Setting up libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Setting up fakeroot (1.20.2-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Setting up android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Setting up android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Setting up click-ubuntu-policy (0.1) ...
Setting up kpartx (0.5.0-7ubuntu4) ...
Setting up ubuntu-snappy-cli (1.5ubuntu1) ...
Warning: The home directory /nonexistent you specified can not be accessed: No such file or directory
Adding system user `snappypkg' (UID 111) ...
Adding new group `snappypkg' (GID 124) ...
Adding new user `snappypkg' (UID 111) with group `snappypkg' ...
Not creating home directory `/nonexistent'.
Setting up ubuntu-device-flash (0.30-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
ventrical@ventrical-MS-7850:~$ 

Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
ventrical@ventrical-MS-7850:~$ 

Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
ventrical@ventrical-MS-7850:~$ 

Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-snappy-cli
Suggested packages:
  debian-keyring
The following NEW packages will be installed:
  android-tools-adb android-tools-fastboot binfmt-support click-ubuntu-policy
  debsig-verify fakeroot kpartx libfakeroot libxmltok1 qemu-user-static
  ubuntu-device-flash ubuntu-snappy-cli
0 upgraded, 12 newly installed, 0 to remove and 252 not upgraded.
Need to get 9,050 kB/10.9 MB of archives.
After this operation, 98.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily/universe qemu-user-static amd64 1:2.3+dfsg-5ubuntu5 [7,248 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily/main kpartx amd64 0.5.0-7ubuntu4 [23.3 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) wily/universe ubuntu-device-flash amd64 0.30-0ubuntu1 [1,778 kB]
Fetched 9,050 kB in 21s (418 kB/s)                                             
Selecting previously unselected package binfmt-support.
(Reading database ... 138325 files and directories currently installed.)
Preparing to unpack .../binfmt-support_2.1.5-1_amd64.deb ...
Unpacking binfmt-support (2.1.5-1) ...
Selecting previously unselected package libxmltok1.
Preparing to unpack .../libxmltok1_1.2-3build3_amd64.deb ...
Unpacking libxmltok1 (1.2-3build3) ...
Selecting previously unselected package debsig-verify.
Preparing to unpack .../debsig-verify_0.13_amd64.deb ...
Unpacking debsig-verify (0.13) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.20.2-1ubuntu1) ...
Selecting previously unselected package qemu-user-static.
Preparing to unpack .../qemu-user-static_1%3a2.3+dfsg-5ubuntu5_amd64.deb ...
Unpacking qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Selecting previously unselected package android-tools-adb.
Preparing to unpack .../android-tools-adb_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package android-tools-fastboot.
Preparing to unpack .../android-tools-fastboot_4.2.2+git20130218-3ubuntu41_amd64.deb ...
Unpacking android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Selecting previously unselected package click-ubuntu-policy.
Preparing to unpack .../click-ubuntu-policy_0.1_all.deb ...
Unpacking click-ubuntu-policy (0.1) ...
Selecting previously unselected package kpartx.
Preparing to unpack .../kpartx_0.5.0-7ubuntu4_amd64.deb ...
Unpacking kpartx (0.5.0-7ubuntu4) ...
Selecting previously unselected package ubuntu-snappy-cli.
Preparing to unpack .../ubuntu-snappy-cli_1.5ubuntu1_amd64.deb ...
Unpacking ubuntu-snappy-cli (1.5ubuntu1) ...
Selecting previously unselected package ubuntu-device-flash.
Preparing to unpack .../ubuntu-device-flash_0.30-0ubuntu1_amd64.deb ...
Unpacking ubuntu-device-flash (0.30-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for man-db (2.7.2-1) ...
Setting up binfmt-support (2.1.5-1) ...
Setting up libxmltok1 (1.2-3build3) ...
Setting up debsig-verify (0.13) ...
Setting up libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Setting up fakeroot (1.20.2-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up qemu-user-static (1:2.3+dfsg-5ubuntu5) ...
Setting up android-tools-adb (4.2.2+git20130218-3ubuntu41) ...
Setting up android-tools-fastboot (4.2.2+git20130218-3ubuntu41) ...
Setting up click-ubuntu-policy (0.1) ...
Setting up kpartx (0.5.0-7ubuntu4) ...
Setting up ubuntu-snappy-cli (1.5ubuntu1) ...
Warning: The home directory /nonexistent you specified can not be accessed: No such file or directory
Adding system user `snappypkg' (UID 111) ...
Adding new group `snappypkg' (GID 124) ...
Adding new user `snappypkg' (UID 111) with group `snappypkg' ...
Not creating home directory `/nonexistent'.
Setting up ubuntu-device-flash (0.30-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (224-1ubuntu3) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
ventrical@ventrical-MS-7850:~$ 

```

after you enable Canonical Partners and install ubuntu-device-flash.

regards..
[CODE]

---

### Post by QDR06VV9 on 2015-09-16
Thanks Again
I did not need [COLOR=#000000]Canonical Partners enabled?
Well lets see how this one goes.

[/COLOR]

---

### Post by ventrical on 2015-09-16
> **runrickus said:**
> Thanks Again
I did not need [COLOR=#000000]Canonical Partners enabled?
Well lets see how this one goes.

[/COLOR]

Interesting. Good luck. I'll back in a bit to check in :)

regards..

---

### Post by ventrical on 2015-09-16
Updating my snappy USB install and version (94) is also busted. It will not update the kernel in GRuB. Looks like this is an across the board problem for Snappy Personal that does not run through the kvm method.

Perhaps waiting for the next  update to version is the solution instead of trashing install.

Regards..

---

### Post by grahammechanical on 2015-09-16
In the thread about desktop next I see that pixelo added a link to where the personal_x86 image comes from. At least I think it is where these images are coming from.

[https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/](https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/)

Interesting that one of the directories is called "rolling."

When I need to download a new image I use the command that ventrical listed in an earlier post. I have broken Personal on USB a few times by forceably removing the USB stick. Now I use shutdown -h instead. My install of Personal has not updated to the 4.2 kernel. So, I did not see that error with today's update.

---

### Post by QDR06VV9 on 2015-09-16
> **ventrical said:**
> Updating my snappy USB install and version (94) is also busted. It will not update the kernel in GRuB. Looks like this is an across the board problem for Snappy Personal that does not run through the kvm method.

[U]Perhaps waiting for the next  update to version is the solution instead of trashing install.
[/U]
Regards..
:D he he he    Well i thought i had a bad burn (mkusb) So i reburned to the same results, "No Boot"
But it shows like it installed correctly? I will try again tomorrow.  
> **grahammechanical said:**
> In the thread about desktop next I see that pixelo added a link to where the personal_x86 image comes from. At least I think it is where these images are coming from.

[https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/](https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/)

Interesting that one of the directories is called "rolling."

_When I need to download a new image I use the command that ventrical listed in an earlier post_. I have broken Personal on USB a few times by forceably removing the USB stick. Now I use shutdown -h instead. My install of Personal has not updated to the 4.2 kernel. So, I did not see that error with today's update.
That's is how I was going to go. Thanks for the reassurance!:D
This thread has the best tools to succeed in written context I have found on the net.
Thanks a Mill to you both.;)
regards

---

### Post by ventrical on 2015-09-17
@runrickus

With your experience it is good to have you on  board because usually graham and I are the ones doing these thought experiments and trying to put them into action. There has been a measure of success in that we can confirm behaviours of certain methods of installation -so- with your help it may roll along even smoother.:) Oh .. and yes .. by no means to I claim to be a unity8 master :) I'm just trying to get it to work like all others are on this project.

regards..

---

### Post by ventrical on 2015-09-17
Ok.. I wiped my original install and reinstalled (88) image, restored it to disk .. updated and it came back again with a grub/uefi error .. Not enough disk space .. so I am going to downlaod new image and try again.

---

### Post by QDR06VV9 on 2015-09-17
Eureka!! Struck payload..
This Install was created with **mkusb 10.1.1** unstable to a 16 gig sandisk thumb drive.
Albeit slow progress it is progress non the less.(Still in infant state of develoment.)
As Grahm pointed out earlier, No way that i could find a way to sign-in to the encrypted wi-fi and all 4 of my  Lans(Eth0) were tied up so I never tried that, But presume that it will work. I and will give that a go later today.


There was a package that I saw yesterday that was suposed to to get the wi-fi up, And I will also check that out later today.
Vent this is cause to be a little ramped-up over, As the features they do have all work.  


Also worth noteing here when D-loading the image this morning i had noticed a difference in how it was being done and went something to this effect.
1.First file was called as such and it was **84.89MB in size**.
2.Second completed file was completed and was **465.03MB**(i am guessing system?)
3.Third file was the generic kernel, size was **41.70MB**
4.Fourth was named icon pkg and was** 38.97MB** in size.(fonts and icons)


When veiwing the thumb drive just parked in the USB i was able to see the 3 Files **1.writable 2.system-b 3.system-a**


Oh as as a side note with the link Grahm had in one of his posts for webmd I was able to save that package and will try to install that today also.
Kind Regards

---

### Post by ventrical on 2015-09-17
Congrads... Yeah .. the browser and the unity8 desktop work pretty fast with mouse n click.  I am doing complete image update. I am not trying to be negative but expect breakage . :) 

Regards..

*note*  of caution. Be careful switching your USB from one PC to another (same for hdd) I am of the thinking that this is what may be breaking my installs..

---

### Post by QDR06VV9 on 2015-09-17
> **ventrical said:**
> Congrads... Yeah .. the browser and the unity8 desktop work pretty fast with mouse n click.  I am doing complete image update. I am not trying to be negative but expect breakage . :) 

Regards..

*note*  of caution. Be careful switching your USB from one PC to another (same for hdd) I am of the thinking that this is what may be breaking my installs..
This image was D-loaded this morning so you should be Ok?(Hope I did not put the Whammy on you;)) 
So far it will boot on Lenovo B-570 && Acer-5750 both are Intel's Lappys
Regards

---

### Post by grahammechanical on 2015-09-17
File Manager on the desktop will show 3 partitions but in actual fact there are 5 partitions as the Disks utility will show. There are 2 boot partitions. One for BIOS boot and one for EFI boot. Whichever fits the hardware running the USB stick.

I found this useful for getting a better understanding of how snappy transactional updates work.

[https://developer.ubuntu.com/en/snappy/guides/filesystem-layout/](https://developer.ubuntu.com/en/snappy/guides/filesystem-layout/)

[https://developer.ubuntu.com/en/snappy/guides/transactional-updates/](https://developer.ubuntu.com/en/snappy/guides/transactional-updates/)

Regards.

---

### Post by QDR06VV9 on 2015-09-17
@grahammechanical How Coincidental:D just about to post these as helpers(future and current)

Here is a few of semi-useful sites for Snappy Personal Desktop.


[http://carla-sella.blogspot.ca/2015/07/snappy-personal-desktop.html](http://carla-sella.blogspot.ca/2015/07/snappy-personal-desktop.html)


[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Snappy-Desktop-Progress](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Snappy-Desktop-Progress)


Hopefully Will Cooke will keep this one current.
[https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo](https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo)


Important info


[https://developer.ubuntu.com/en/snappy/guides/filesystem-layout/](https://developer.ubuntu.com/en/snappy/guides/filesystem-layout/)


And for Transactional system updates


[https://developer.ubuntu.com/en/snappy/guides/transactional-updates/](https://developer.ubuntu.com/en/snappy/guides/transactional-updates/)


And for Devs.
[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)


These are just the ones I have found that seem to be meaningful, At least in my IMHO. Will update this as I find more Good and credible ones.
Thank You Sir;)

---

### Post by ventrical on 2015-09-17
> **runrickus said:**
> This image was D-loaded this morning so you should be Ok?(Hope I did not put the Whammy on you;)) 
So far it will boot on Lenovo B-570 && Acer-5750 both are Intel's Lappys
Regards

It is booting good with webdm. Had to to full image update. Will do the same on USB.

Regards..

---

### Post by QDR06VV9 on 2015-09-17
Have you two seen this yet?
[https://uappexplorer.com/apps?type=snappyComes](https://uappexplorer.com/apps?type=snappyComes) 
With This Discription
> Welcome to uApp Explorer!
This site is an unofficial app browser for Ubuntu Touch apps. All data for the apps comes from a publicly accessible api. This site is maintained by Brian Douglass and is not endorsed by or affiliated with Ubuntu or Canonical. Ubuntu and Canonical are registered trademarks of Canonical Ltd.
Let me know what you think.
regards

---

### Post by ventrical on 2015-09-18
> **runrickus said:**
> Have you two seen this yet?
[https://uappexplorer.com/apps?type=snappyComes](https://uappexplorer.com/apps?type=snappyComes) 
With This Discription

Let me know what you think.
regards

Looks like it is in the spirit of open source. Uh.. wouldn't it defeat the purpose of the 'snappy' transactional update security repos though? Just having a tough time wrapping my head around some of the slated changes commign down the pipe and what their full meanings are.

regards..

---

### Post by grahammechanical on 2015-09-18
I checked out the web site and I might try it the next time I boot Personal. They do say on that site that it does not actually download or install the app but it triggers the Ubuntu app store.

FAQ

> To install an app, visit this site on your Ubuntu Touch device. Find the app     that you wish to install and click the "Install" button. You will then be     taken to the official appstore on your device where you can install the app.     
    Apps are not installed via this site, but via the official appstore.

Regards.

---

### Post by QDR06VV9 on 2015-09-18
Last nite I wiped a Vivid partition and Installed Unity and D-loaded a fresh personal.img.
Wanted to have a look at QEMU and just play around.
Here is what my new .img looks like.(See Attachment)
Can not get past the first screen though, Going to try again in a few hours. Boy it looks like a little action is going on though, Due to heavy traffic the sever was under got bumped off a couple of times last nite before I got a successful .img  

> Looks like it is in the spirit of open source. Uh.. wouldn't it defeat the purpose of the 'snappy' transactional update security repos though?  Just having a tough time wrapping my head around some of the slated changes commign down the pipe and what their full meanings are.

As grahammechanical pointed out just triggers app store.
Kind of like a browser mode for apps with a better understanding or discription.
But yes I too find it a bit over whelming with all the new stuff(at least to me:D)
But that is the reason we are here. Kind of has my interest peaked again.

>  Discover apps for you Ubuntu Touch device
This is an official webapp for uappexplorer.com. With uApp Explorer you can browse and install apps for Ubuntu Touch.

**Why use this over the built in appstore? It has many features that the built in store does not have, like being able to tell if an app is just a webapp, sort apps by rating, and more! **You can browse by category, type, and app author.
Regards

---

### Post by QDR06VV9 on 2015-09-18
So QEMU is kind of worthless on that image, so I went with installing to USB via **mkusb 10.2 unstable **still not useable(**image not mkusb**) no way to login.
But i was able to catch a bug and was filed here [https://bugs.launchpad.net/ubuntu/+source/systemd/+filebug/7dcc9e14-5e22-11e5-91eb-002481e7f48a?field.title=systemd-udevd%20crashed%20with%20SIGABRT%20in%20__open_nocancel%28%29](https://bugs.launchpad.net/ubuntu/+source/systemd/+filebug/7dcc9e14-5e22-11e5-91eb-002481e7f48a?field.title=systemd-udevd%20crashed%20with%20SIGABRT%20in%20__open_nocancel%28%29)
Has already been reported though.
Bug showed
> systemd-udevd crashed with SIGABRT in __open_nocancel()
systemd must be keeping them very busy with Triaging .
I'm going to watch Vent work his tablet over for a bit.:D

---

### Post by ventrical on 2015-09-18
> **runrickus said:**
> So QEMU is kind of worthless on that image, 

It varies from machine to machine. It will work on older Code 2 Duo processors with nVidia, and later Intel based family 9 haswell graphics - and then it just won't work at all. Finicky with QEMU.


> so I went with installing to USB via **mkusb 10.2 unstable **still not useable(**image not mkusb**) no way to login.
But i was able to catch a bug and was filed here [https://bugs.launchpad.net/ubuntu/+source/systemd/+filebug/7dcc9e14-5e22-11e5-91eb-002481e7f48a?field.title=systemd-udevd%20crashed%20with%20SIGABRT%20in%20__open_nocancel%28%29](https://bugs.launchpad.net/ubuntu/+source/systemd/+filebug/7dcc9e14-5e22-11e5-91eb-002481e7f48a?field.title=systemd-udevd%20crashed%20with%20SIGABRT%20in%20__open_nocancel%28%29)
Has already been reported though.
Bug showed

systemd must be keeping them very busy with Triaging .
I'm going to watch Vent work his tablet over for a bit.:D


```

sudo service lightdm restart

```

works often for me.

> 
I'm going to watch Vent work his tablet over for a bit.:grin:

Perhaps I will be able to brick RCA tablet # 2 :)

Regards..

---

### Post by QDR06VV9 on 2015-09-18
> [COLOR=#000000]sudo service lightdm restart[/COLOR]
[COLOR=#000000]I did that and still nothing.
Your absolutely right about the Intel Chips, have yet to get QEMU to work on my AMD Quad.[/COLOR];)[COLOR=#000000] 
Both of my Lappy's are Intel Core 2 Hyper-thread with Intel Graphics, And no issues with those.
I'll get the AMD Quad working with snappy. I'm determined![/COLOR]:D
Regards

---

### Post by ventrical on 2015-09-18
> **runrickus said:**
> [COLOR=#000000]I did that and still nothing.
Your absolutely right about the Intel Chips, have yet to get QEMU to work on my AMD Quad.[/COLOR];)[COLOR=#000000] 
Both of my Lappy's are Intel Core 2 Hyper-thread with Intel Graphics, And no issues with those.
I'll get the AMD Quad working with snappy. I'm determined![/COLOR]:D
Regards

My AMD Attlon 2x 6000 is faster than my intel quads. I have yet to try it with snappy.

---

### Post by QDR06VV9 on 2015-09-19
Decided to see what errors were shown in the terminal after launching QEMU and was suprised to see security warning.
See Attachments.
And stops There.
So maybe I wont get snappy to work on my 
> Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4a svm) 
           Clock Speeds: 1: 2600.00 MHz 2: 2600.00 MHz 3: 2600.00 MHz 4: 2600.00 MHz

 I have Athlon 2x 6000 still setting in a box (Barely used Tower)
 Think I will break that out play with it this weekend.
 Regards

---

### Post by ventrical on 2015-09-19
> **runrickus said:**
> Decided to see what errors were shown in the terminal after launching QEMU and was suprised to see security warning.
See Attachments.
And stops There.
So maybe I wont get snappy to work on my 


 I have Athlon 2x 6000 still setting in a box (Barely used Tower)
 Think I will break that out play with it this weekend.
 Regards

I have received that error several time with kvm on machines with low memory and high memory alike. Not sure what it is . I think it may be transition in the works.

regards..

edit:

Nope ... tried a few different things ... loads up but no desktop, infinite boot to lightdm etc..

---

### Post by QDR06VV9 on 2015-09-19
> [COLOR=#000000]Nope ... tried a few different things ... loads up but no desktop, infinite boot to lightdm etc..[/COLOR]
Yes so Close but yet so far away. :D I like challenges like this!(Fiendish Grin.)
You know a thought just came to me, Most of the devices that snappy is meant for are [B]Intel's.
[/B]Instruction Sets??
Regards

---

