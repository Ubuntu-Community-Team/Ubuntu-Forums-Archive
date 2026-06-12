---
title: "Upgrade or Fresh Install?"
date: 2009-11-30
forum: Ubuntu Studio
---

### Post by bigsmitty64 on 2009-11-30
Hey,I've been using Ubuntu 9.10 for a few days now,and love it.However I am a musician and have just found and downloaded 9.10 Studio amd64. Question is do I upgrade or do a fresh install? Once I mounted the iso it asked me if I wanted to upgrade,but I wasn't sure if a fresh install would be better. Just trying to keep it as simple as possible. Thanks in advance for any help.
P.S. I am a complete newbie to linux,but so far the learning curve hasn't been TOO bad.
Smitty

---

### Post by fancypiper on 2009-11-30
I would try just installing the audio programs before I would do a re-install.

# Install lots of multimedia programs
sudo apt-get install ubuntustudio-audio*

---

### Post by AutoStatic on 2009-11-30
Neither upgrade nor install. Just install the software you want with Synaptic, everything that is in Ubuntu Studio is also available for plain Ubuntu.

---

### Post by Scott L on 2009-11-30
Neither of the two previous replies mentions the real-time kernel and therefore sound like incomplete suggestions.

If you are serious about multimedia production (especially audio) then don't muck about and do a fresh install of Ubuntu Studio.  It will include such things as the real-time kernel plus have other things configured such as the audio group.

---

### Post by snowpine on 2009-11-30
'sudo apt-get install linux-rt' will give you the real time kernel.

'sudo apt-get install ubuntustudio-default-settings' will give you the default settings.

---

### Post by bigsmitty64 on 2009-11-30
Thanks for the suggestions,
 as far as just getting the settings and audio through the terminal,
wouldn't it be just as easy to insert my studio DVD and take the upgrade
that comes up?

---

### Post by AutoStatic on 2009-11-30
That's a possibility.
I would follow Snowpine's advise though, you can do that with Synaptic also, just do a search for 'linux-rt' and 'ubuntustudio-default-settings' and install those packages. This will save you a lot of time.

---

### Post by waspbr on 2009-11-30
yep, synaptic is your friend here, just search for ubuntustudio and look at the results, you can cherry pick what you want to install, either that be audio package, the video package, or the whole ubuntustudio-desktop which includes the themes, sounds and whatnot.

---

### Post by AutoStatic on 2009-11-30
This will save you from having to update packages also because there will probably reside some packages on the DVD that have had an update in the meanwhile.

---

### Post by bigsmitty64 on 2009-12-01
O.K. , I got these,

sudo apt-get install ubuntustudio-audio

sudo apt-get install linux-rt

ubuntustudio-default-settings

Everything seems good.Should I get anything else? I don't really care about the wallpapers and icons,I can change that stuff myself.
What about Jack? I noticed a couple programs require this.Is it just a sound driver of sorts?

---

### Post by fancypiper on 2009-12-01
You should have ubuntustudio installed, including Jack.

[What is JACK?]("http://jackaudio.org/") Essentially it is an audio connection kit

---

### Post by trulan on 2009-12-01
Didn't Jack (jackd) come with the ubuntustudio-audio package?

It's a sound server - (all the REAL audio programs use it) (okay, maybe not, I'm biased, I know...) that enables you to connect audio from anywhere to anywhere.  Just like plugging wires from one piece of sound equipment to another, jack lets you 'plug wires' between your audio applications.

Don't forget the ubuntustudio-audio-plugins package.  I'd be lost without that.

For a good look at the other metapackages available, open Synaptic and type ubuntustudio in the search bar.

---

### Post by bigsmitty64 on 2009-12-01
Fancy,
thanks for the link. It will prove quite useful

trulan,
 yes Jack did come with the package(my bad for not looking first!)

I installed the audio plugin package,and I know what plugins are and how they work,but I don,t see the package anywhere in, applications/sound and video.Do they go into the individual programs automatically?

---

### Post by fancypiper on 2009-12-01
98% (estimated) of the apps installed will be in the menu but the plug-ins show up in the preferences of the app the plug-in is for.

Right click on the panel applications and you can edit the menu and add/remove what you wish.

To find things in Linux, use locate first.

Example: sound-juicer didn't show up automatically in my setup, so I used locate to find out where the binary is:

phil@tinwhistle ~ $ locate sound-juicer|grep bin
/usr/bin/sound-juicer

Aha! it's in /usr/bin as I suspected. Binary files reside in a directory/subdirectory /bin, root binaries reside in a directory/subdirectory /sbin

I can now add sound-juicer to the applications>sound menu and choose an icon with the clicks.

HTH

---

### Post by trulan on 2009-12-02
The plug-ins will show up in the programs that use them, as fancypiper said.  For instance, Audacity should now have several hundred plug-ins in its menu, as opposed to several dozen.

Jack-Rack is an easy way to host plug-ins to use with Jack.  Also, the Calf plug-in pack comes with its own host for Jack, including an excellent gui.  Once Jack is up and running (Use Jack Control for that), open Jack Rack or the Calf Pack, then open Patchage and route your sound through your plug-ins.

That is all assuming you already have Jack configured properly.  If not, search around, there's a lot of good info on configuring Jack already out there.  If you have troubles, you know where to ask.  ;)

---

### Post by Scott L on 2009-12-02
> **fancypiper said:**
> You should have ubuntustudio installed, including Jack.

[What is JACK?]("http://jackaudio.org/") Essentially it is an audio connection kit

I have been working on the Ubuntu Studio documentation, you can find it here:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

Specifically, you mentioned JACK, which I you can find what I consider a nice littler write up similarly titled as your link:
[https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

---

### Post by Scott L on 2009-12-02
> **snowpine said:**
> 'sudo apt-get install linux-rt' will give you the real time kernel.
  
  'sudo apt-get install ubuntustudio-default-settings' will give you the default settings.

> **AutoStatic said:**
> That's a possibility.
I would follow Snowpine's advise though, you can do that with Synaptic also, just do a search for 'linux-rt' and 'ubuntustudio-default-settings' and install those packages. This will save you a lot of time.

Last night using a VM I tested installing the ubuntustudio-default-settings from a plain, vanilla Ubuntu install and found that it did not include the user in the audio group.  Nor did it change any settings in the /etc/security/limits.conf file.

So some of your inferences are slightly disingenuous.

I will be working on the documentation for upgrading from a plain, vanilla Ubuntu to Ubuntu Studio very soon at:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

To state it openly, it is beneficial to add the user to the audio group.

Then the /etc/security/limits.conf can have additional entries added, for example:[FONT=monospace]
[/FONT]@audio - rtprio 99
@audio - nice -10[FONT=monospace]
[/FONT]@audio - memlock unlimited

This will facilitate users in the audio group to maximize the rt kernel and ensure that applications have enough memory allocated to them which in all should help reduce any dropped audio that is being recorded.

Also note that edit the limits.conf file should be done as root.

Sorry that this post is rather direct and to the point but I am replying from work.

Regards.

---

### Post by AutoStatic on 2009-12-02
> **Scott L said:**
> Last night using a VM I tested installing the ubuntustudio-default-settings from a plain, vanilla Ubuntu install and found that it did not include the user in the audio group.  Nor did it change any settings in the /etc/security/limits.conf file.

So some of your inferences are slightly disingenuous.That's right, you have to change those settings manually or with the help of Ubuntu Studio Controls, which is still a bit buggy unfortunately. And besides, the question was 'upgrade or fresh install?' and not 'what is the best way to get my system rt audio ready?' ;)

---

### Post by bigsmitty64 on 2009-12-02
> **AutoStatic said:**
>  the question was 'upgrade or fresh install?' and not 'what is the best way to get my system rt audio ready?' ;)

BY all means,carry on! haha! This is a great help. I have everything working now I think.Now to figure out how to use it all! WOW! I am amazed at the amount of stuff in Studio.The plugins are crazy! I've had Audacity in windows for quite some time,and love it,but man, the amount of plugins in that alone are insane! I can't wait to start recording some tunes! Thanks everyone for the help with everything.

Smitty.

---

### Post by trulan on 2009-12-02
Hey, glad things are going well for you!  There's a lot to learn, that's for sure.  And the possibilities are pretty much limitless.  It's the beauty and the problem of open source software.  But the Ubuntu Studio team has been doing a great job of easing the learning curve.

Best of luck to you Smitty!

---

### Post by AutoStatic on 2009-12-03
> **bigsmitty64 said:**
> BY all means,carry on! haha! This is a great help.Good thing that you got it all working! And I was being a bit sarcastic, I know, sorry about that.

---

### Post by bigsmitty64 on 2009-12-06
I got everything working and then woke up this morning to a  "reboot to install updates" message. So I reboot,or TRY to. Right after chose Ubuntu in my dual boot screen I got a screen black screen with something about grub.

```
[Minimal BASH- like line editing is supported. For the first word. TAB list possible command completions. Anywhere else TAB list possible device/ file completions] 

sh.grub>
```I have since read all the threads on the forum about it,but I had already uninstalled by then. I ended up installing Studio 9.10 and am quite happy.

---

