---
title: "Ubuntu next"
date: 2015-05-18
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2015-05-18
A also made the mistake of getting the **ubuntu-desktop-next** image and wondering what to do with it.

I installed it in VirtualBox and when the live system started it went to a login screen that did not manage to move to a desktop using ubuntu as username and leaving blank as password.
I then tried using the Install option from booting the .iso file, chose to autologin, and that managed to get to an empty screen with just my username showing, but it was not quite like a login screen, with no box for a password to be typed, and once again I could do nothing with it; no keyboard shortcuts worked, eg Ctrl+Alt+T did not get a terminal.

I gave up and used zsync to convert the .iso file into the standard version.  That installed incredibly fast and for the moment is running like a demon, fast and smooth as anything I've tried, though I am aware that it is not yet very different from the 15.04 version.

So the original question remains;  how can one do anything at all with the** ubuntu-desktop-next** image?
I am aware of the login greeter screen bug which requires using Ctrl+Alt+F1 to get to a tty, but in VBox that always takes me to a tty of the host, not the guest, so is no help at all.
Perhaps I could have booted to a text command line from grub by changing "quiet splash" in the kernel line to "text" but I could not be bothered to try that, having already spent too much time playing around.

Any thoughts anyone?

---

### Post by grahammechanical on 2015-05-18
I last installed desktop next on 10th of this month. It was one of the first Wily images. And like any hard disk install I was required to set a user name and password. It loaded to a lightdm login screen and the password that I have set was sufficient. It then when to a phone system login screen and the same password worked.

I agreee that there is not much that can be done with it. But it does logout and shut down which it never used to do. As we are going to be getting snappy personal I consider desktop next to be a dead end or a curiosity.

I think that when we install desktop next in LXC that the user name is ubuntu and the password is ubuntu.

Regards.

---

### Post by ventrical on 2015-05-19
> **grahammechanical said:**
> I last installed desktop next on 10th of this month. It was one of the first Wily images. And like any hard disk install I was required to set a user name and password. It loaded to a lightdm login screen and the password that I have set was sufficient. It then when to a phone system login screen and the same password worked.

I agreee that there is not much that can be done with it. But it does logout and shut down which it never used to do. As we are going to be getting snappy personal I consider desktop next to be a dead end or a curiosity.

Regards.

  I was very enthusiastic when I was experimenting with mir and unity8. I thought it was a good idea. It still is a good idea bit it is not feasible , really, as a working man's desktop, to have to navigate around an executive play thing. Snappy may offer promise of presenting a more realistic desktop/phone convergence concept for users on the go.

Regards..

---

### Post by grahammechanical on 2015-05-19
Last night after reading this thread I decided to go into that 10th May desktop next install and update/upgrade it. I got into the OS just fine and I used the terminal app to update/upgrade and towards the end of the upgrade the screen went black with just a white cursor arrow. And now when I restart and make the switch from lightdm login to Mir and the phone OS login all I get is the black screen with the white cursor. Just like the old days.

My earlier vivid desktop next ended up with kernel panic. I do not want to point the finger at systemd as I am having no problems with desktop Wily but it is now part of the mix. I think that going back to the beginning as the devs are doing with Ubuntu Snappy Personal is indeed the best course of action.

Regards.

---

### Post by Cavsfan on 2015-05-20
Is there something that is telling the system that I'm using a phone instead of a PC? Because every install since Trusty wants to keep only one kernel:
Unless I edit the **/etc/apt/apt.conf.d/01autoremove-kernels** file after deleting the 3rd oldest kernel I would end up with only one kernel.

[http://ubuntuforums.org/showthread.php?t=2251168](http://ubuntuforums.org/showthread.php?t=2251168)

Here is the bug I filed and it only has 3 people on it, which I do not understand.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1440608](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1440608)

---

### Post by zika on 2015-05-20
Better place to look_at/edit is /etc/kernel/postinst.d/apt-auto-removal ...

---

### Post by Cavsfan on 2015-05-20
> **zika said:**
> Better place to look_at/edit is /etc/kernel/postinst.d/apt-auto-removal ...

I'm not a programmer or at least not this language.

But I did see this in that file: 
```
    # We have at least two kernels that we have reason to think the
    # user wants, so don't save the second-newest version.

```

It sort of jumps around. After a new kernel is installed in this case 18, the file says keep 17 and 18. 

Then when you purge 16 it changes to 16 and 18, thus making 17 eligible to be auto-removed. 

But if you auto-remove 17 or even manually delete it, you only have the 18 kernel with no backup.
Not that I've ever had a need or use for an older kernel I thought it should keep two like it has in the past.

---

### Post by zika on 2015-05-20
Check if You've (even unintentionally) changed kernel-package(s) flag(s) (automatically/manually-installed)...

---

### Post by Cavsfan on 2015-05-20
> **zika said:**
> Check if You've (even unintentionally) changed kernel-package(s) flag(s) (automatically/manually-installed)...

I never touch anything with the kernels. I just install them in updates. But, there was something that I changed a while back that perhaps *could* be causing this.

I was using **alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean' **
And an admin said that would purge packages that might need to be re-downloaded and for someone with slow internet access that would hurt them.

I have a fast internet connection so I never worried about it. But I changed it to **alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'**

Since then (me thinks) I have been seeing things like this when I run that command:
(This is on Trusty but all my versions got kernel updates today and all my versions do this too)
```
Reading state information... Done
Del linux-libc-dev 3.13.0-52.86 [773 kB]
Del linux-image-generic 3.13.0.52.59 [2,350 B]
Del linux-headers-generic 3.13.0.52.59 [2,334 B]
Del linux-generic 3.13.0.52.59 [1,786 B]
```

Could that be what is causing it on Trusty, and Wily?

I changed the alias back to what it was before. I'll see if that makes any difference. I see packages deleted everytime I update and I didn't use to.

---

### Post by zika on 2015-05-20
No. That is not, by any means, connected.

---

### Post by Cavsfan on 2015-05-20
> **zika said:**
> No. That is not, by any means, connected.

I understand your point - the differences between clean and autoclean do not in any way point to the symptoms I have. But this never happened on Trusty before.
And now on every system I have touched it happens. That is about the same time this started happening to me and another person that changed that alias.

Oh well just for the halibut I'll see what happens the next time a kernel comes down the trough. :p

---

### Post by bapoumba on 2015-05-21
Off topic posts moved to their own thread.

---

### Post by ventrical on 2015-05-21
> **grahammechanical said:**
> Last night after reading this thread I decided to go into that 10th May desktop next install and update/upgrade it. I got into the OS just fine and I used the terminal app to update/upgrade and towards the end of the upgrade the screen went black with just a white cursor arrow. And now when I restart and make the switch from lightdm login to Mir and the phone OS login all I get is the black screen with the white cursor. Just like the old days.

My earlier vivid desktop next ended up with kernel panic. I do not want to point the finger at systemd as I am having no problems with desktop Wily but it is now part of the mix. I think that going back to the beginning as the devs are doing with Ubuntu Snappy Personal is indeed the best course of action.

Regards.

"I do not want to point the finger at systemd..."

I was doing a clean install of 14.04 on a clients machine from the 14.04.1 release. I update/upgrade/rebooted and after hard shutdown-startup it started regurgitating  lines and lines of verbose "systemd_udev_error" or something to this effect! I thought .. 'what is systemd doing on 14.04.2?'

*note to mods* please let this semi off topic comment ride.. I hope to have a point to make later that is topical to this thread.

Edit: Yep .. systemd is the culprit ... but the daily 05/21/2015 is in much better shape in 'live' mode though. Looks like some serious progress but most of the gestures have changed again but it sort of guides you along in the 'live' mode with helper/reminders. For example .. this floating unity-like side-bar oscilating panel moving in and out has to be "swiped" very curtly and swiftly (with the mouse) for it to work. But the apps that were available with Utopic are not available now. It looks like a serious reconstruction top-down _  bottom up. I am going to hard install. We have to test and experiement because  it looks like it could be a decent desktop (non-touch) alternative.

@grahammechanical

Yes .. there was the 'white arrow of mir' (sounds like a good title for a Harry Potter prequel-and don't think it can't happen)lol .. but after I waited a while it went right to the phone desktop with floating unity panel after I entered "ubuntu' as password.

Regards...

---

### Post by ventrical on 2015-05-21
re: white arrow of mir:

I did a hard install and got the white arrow of mir. But I waited. There is a delay. It looks like the screen is locked with White Arrow of Mir but after a while the phone log on will pop up and it will take you on a guided tour.  On the lower right corner you will see <cont> so you have to keep clicking that until tou are congradulated and Finished!

Progress indeed.. ahem .. :)

It must be systemd waiting to start a service. I tired to install Nick's terminal app but it will not install.. it wants Ubuntu One logon .. not SSO.

Regards..

---

### Post by ventrical on 2015-05-22
Starts up.
Shuts down.
Browser broken.
Notepad works.

The Ubuntu App Store only works once and when you try to install something it will break. Then, if you try it ,it will just spin, appear that it is downloading something and do nothing.

Upstart is available in grub - works faster than systemd and no verbose errors.

Using 'top' in terminal shows that it is using 'unity-system-compositor'. There is no GUI option to use x.

Regards..

---

### Post by ventrical on 2015-06-02
I just found this article. It claims that Ubuntu-desktop-next 15.10 will be using snappy for sure.

[https://news.ycombinator.com/item?id=9515156](https://news.ycombinator.com/item?id=9515156)

Regards..

---

### Post by grahammechanical on 2015-06-03
Something is said about it in this week's Community Q & A. I cannot remember what exactly.

[https://www.youtube.com/watch?v=oYs1r8Lns-s](https://www.youtube.com/watch?v=oYs1r8Lns-s)

If 16.04 is going to have both a Debian packaged/apt-get version of Ubuntu desktop (just like at present) and a version with snap packaging and transactional updates then it would make logical sense to get ISO images of the snappy version out here well before the 16.04 release date. Even if the install is of limited usefulness.

Some other things to consider. a) Ubuntu phone was built on the Utopic development code base and is now being transitioned on to Vivid. b) Ubuntu phone has Click packaging. c) Ubuntu phone will convert to Snap packaging. d) This year we will have a Ubuntu phone that is a converged device. One blogger gave a date as the "end of October." Others say, by the Fall or this year.

Could this converged device be built on Wily code? And will there be a Wily desktop ISO image by the time the converged device is released or even sooner? I think so. A converged device will not be much good if all it does is turn a digital TV into a mobile phone. So, the release of a converged device and Ubuntu Desktop running on Mir and snappy do have to be developed at the same time.

Regards.

---

### Post by ventrical on 2015-06-03
> **grahammechanical said:**
> 

Could this converged device be built on Wily code? And will there be a Wily desktop ISO image by the time the converged device is released or even sooner? I think so. A converged device will not be much good if all it does is turn a digital TV into a mobile phone. So, the release of a converged device and Ubuntu Desktop running on Mir and snappy do have to be developed at the same time.

Regards.


It is assumed that all of the above will be made so. So far we are only being fed a few biscuits here and there. Nothing to bite into. No meat and potatoes so to speak. The snappy internet of things, gizzmos and whatchamajigs is a major undertaking. Summer is near upon us. Devs will get bored.  I hope we get a snappy personal .iso before June is done with. Otherwise there is not really much for us testers to do that is adventurous.

Regards..

---

### Post by grahammechanical on 2015-06-05
i am checking cdimage.ubuntu.com almost daily and I notice that the last daily build for ubuntu-desktop-next was 20152905. So, it seems that this version of Ubuntu Next has come to an end. What heading will the first image of Snappy Ubuntu Next be posted under? We wait and see.

Regards.

---

### Post by jerrylamos on 2015-06-07
Just tried the latest Wily Next.  No workee, usual trouble with login, passwords, etc.  I'll try again some day.

---

### Post by pixelro on 2015-06-10
[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/)

what is daily preinstalled and how do you install it? o_O

---

### Post by cariboo on 2015-06-10
> **pixelro said:**
> [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/)

what is daily preinstalled and how do you install it? o_O

There seems to be nothing there to install. This may work better for you:

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

---

### Post by pixelro on 2015-06-11
> **cariboo said:**
> There seems to be nothing there to install. This may work better for you:

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

thanks :> 

hmm now there is also [wily-preinstalled-desktop-next-armhf.tar.gz]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/wily-preinstalled-desktop-next-armhf.tar.gz")

---

### Post by grahammechanical on 2015-06-11
The last ubuntu-desktop-next ISo image was built on 29 May 2015. The pre-installed section does not have ISO images. I guess a person would have to download the archive file, unpack it and create their own ISO image. I have concluded that Ubuntu Desktop Next is not being developed any more.

During Tuesday's Community Q&A (2015-06-09) on Ubuntu On Air I am sure I heard it said that we will be getting an ISO image for Ubuntu Snappy Personal for testing next week or the week after. That image will be the "cuckoo" in the Ubuntu 16.04 nest. 

The information is given about 16 - 17 minutes into the Ubuntu On Air session. I have just listened to it again and I definitely hears these words: "In the next week or two we should have a working snappy based desktop image." for playing around with.

It should have its own thread.

Regards.

---

### Post by QDR06VV9 on 2015-06-11
> **grahammechanical said:**
> The last ubuntu-desktop-next ISo image was built on 29 May 2015. The pre-installed section does not have ISO images. I guess a person would have to download the archive file, unpack it and create their own ISO image. I have concluded that Ubuntu Desktop Next is not being developed any more.

During Tuesday's Community Q&A (2015-06-09) on Ubuntu On Air I am sure I heard it said that we will be getting an ISO image for Ubuntu Snappy Personal for testing next week or the week after. That image will be the "cuckoo" in the Ubuntu 16.04 nest. 

The information is given about 16 - 17 minutes into the Ubuntu On Air session. I have just listened to it again and I definitely hears these words: "In the next week or two we should have a working snappy based desktop image." for playing around with.

It should have its own thread.

Regards.
Funny That was also my conclusion as well that Ubuntu Desktop Next is not being developed any more.
And also agree, Like I have any say, but it should have it's own thread or at the very least using the thread tools marked as snappy!
Thanks for keeping us up to Date on the Q&As Time is my enemy right now, It is great that you at least report back Important Info.
Kind Regards

---

### Post by cariboo on 2015-06-11
> **runrickus said:**
> Funny That was also my conclusion as well that Ubuntu Desktop Next is not being developed any more.
And also agree, Like I have any say, but it should have it's own thread or at the very least using the thread tools marked as snappy!
Thanks for keeping us up to Date on the Q&As Time is my enemy right now, It is great that you at least report back Important Info.
Kind Regards

I agree, and once the images are available, I'm sure one of us will start a new thread.

---

### Post by pixelro on 2015-06-12
[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/)

[wily-preinstalled-desktop-next-amd64.device.tar.gz]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/wily-preinstalled-desktop-next-amd64.device.tar.gz") (amd64 builds)
[https://lists.ubuntu.com/archives/snappy-devel/2015-June/000768.html](https://lists.ubuntu.com/archives/snappy-devel/2015-June/000768.html)

---

### Post by craig10x on 2015-06-13
A new next image?  Thought they were supposed to switch over to snappy this month...

---

### Post by grahammechanical on 2015-06-13
I have been trying to find out the purpose of those daily-preinstalled gzip files. I am coming to the conclusion that they are for OEMs to use for installing Ubuntu on devices before shipping to the retailer and without going through the usual installation process that we experience when installing from an ISO image. I guess they are something that can be flashed to a ROM.

Also, as far as I can tell the new mir/unity8/snappy based Ubuntu desktop is for the time being called Snappy Personal. So, I am keeping an eye on cdimage.ubuntu.com for a new link to Ubuntu Snappy Personal. And anywhere else that I can think of where we might find the new ISO images for Snappy Personal. Over the next two weeks we might see something. Whoever is first to see one of these ISO images please start a new thread.

Regards.

---

### Post by ventrical on 2015-06-13
> **grahammechanical said:**
> I have been trying to find out the purpose of those daily-preinstalled gzip files. I am coming to the conclusion that they are for OEMs to use for installing Ubuntu on devices before shipping to the retailer and without going through the usual installation process that we experience when installing from an ISO image. I guess they are something that can be flashed to a ROM.

Exactly.

> 

Also, as far as I can tell the new mir/unity8/snappy based Ubuntu desktop is for the time being called Snappy Personal. So, I am keeping an eye on cdimage.ubuntu.com for a new link to Ubuntu Snappy Personal. And anywhere else that I can think of where we might find the new ISO images for Snappy Personal. Over the next two weeks we might see something. Whoever is first to see one of these ISO images please start a new thread.

Regards.

The current  snappy image can be installed to a USB but it doesn't do much at all. Same with kvm, a few simple commands.

I also have my eye on the beam, ear to the rail .. but I am willing to bet money that you will be the first to start new thread on this. :)

Regards..

---

### Post by craig10x on 2015-06-14
Looking forward to seeing the new thread on snappy personal desktop when the isos become available and you guys start testing ;)
Do a good job and help them get it ready for prime time (hopefully by the release of 16.04 as they mentioned) :D

---

### Post by Mateusz Stachowski on 2015-06-14
> **grahammechanical said:**
> Also, as far as I can tell the new mir/unity8/snappy based Ubuntu desktop is for the time being called Snappy Personal. So, I am keeping an eye on cdimage.ubuntu.com for a new link to Ubuntu Snappy Personal. And anywhere else that I can think of where we might find the new ISO images for Snappy Personal. Over the next two weeks we might see something. Whoever is first to see one of these ISO images please start a new thread.

Regards.

I don't know from where did you get the idea that there will be a new Ubuntu ISO named Snappy Personal. This won't happen. Ubuntu Desktop Next at one point will simply switch from .deb to snappy packages.

This was in the [post]("https://plus.google.com/u/0/+WillCooke/posts/AxfoU3N1Ezo") from Will Cooke:

> Our plan for 15.10 (which is still being finalised, and will be discussed in more depth at UOS in a couple of weeks) **is to have a build based on Snappy Personal and so the current .deb based Desktop Next image will be going away **and will be replaced with the new Snappy version.

We'll preserve the most recent Desktop Next deb based ISO on cdimage.ubuntu.com (link to follow as soon as it's available).  The future is Snappy and you'll have an image to play with Real Soon Now.

Also there is this [post]("https://plus.google.com/+WillCooke/posts/DxKPdBWWwEs") he made when they build the first Snappy based version of Ubuntu Desktop Next:

> Sebastien Bacher has got a Snappy build of Desktop Next for i386.  We need to turn it into an installable image now, and work out why amd64 didn't work.

---

### Post by grahammechanical on 2015-06-14
Once upon a time there was Ubuntu Touch. Now it is called Ubuntu for Devices. Although confusingly we still see the word "touch" being used. Canonical has a habit of changing the working titles of its software projects.

I see nothing in Will Cook's post to convince me that the name "desktop next" will remain. I do see references to "Snappy Personal" and I have heard that expression used on the Community Q & A by David Panella. He spoke of that expression as a code name used by Canonical developers.

The last daily-live ISO image of Ubuntu Desktop Next on cdimage.ubuntu.com is dated 20150529. And until I see an ISO image in the Ubuntu Desktop Next section with a date in June or July and it turns out to be Ubuntu desktop using Mir, Unity 8 and Snap packaging I will not be convinced that the label "desktop next" will survive the switch. Whatever label these ISO images are given, I would not be surprised if the name changes in the future.

We have Snappy Core but that is for the Cloud and the Internet of Things. I see the use of "Snappy Personal" as a way of distinguishing the snappy desktop from Snappy Core. It is not a name that I have invented. I am just trying to keep up to date with what is happening to Ubuntu on the desktop.

---

### Post by Mateusz Stachowski on 2015-06-14
I agree the naming of Canonical software projects or rather the way the developers refer to those projects changes so much. But I don't see any logical reason to make a new ISO image and if they will make that it will be really stupid, even moronic.

Also Snappy Personal is just the way they refer to desktop/mobile part of snappy.

[http://www.reddit.com/r/Ubuntu/comments/33kybn/an_important_notice_for_ubuntu_desktop_next_users/](http://www.reddit.com/r/Ubuntu/comments/33kybn/an_important_notice_for_ubuntu_desktop_next_users/)

> **popeydc **(this is Alan Pope)
Snappy personal = Ubuntu Desktop image built using Snappy packages. Where Snappy packages are the next evolution on from click packages.


**mhall119** (this is Michael Hall)
Snappy is an evolution of click, which will eventually replace clicks on the phone. Snappy Personal is to phone and desktop what Snappy Core is to cloud and IoT, it's the base install image that provides the minimum functionality needed for you to get started.

---

### Post by ventrical on 2015-06-14
> 

..will cook
The new Ubuntu desktop starts here, and there will be loads of  interesting things to work on so keep an eye on the UOS schedule and  sign up to any sessions you're interested in.&#65279;


Then it's just a bunch of hooey then.  The only thing to work on  are all the busted instances of 15.04 (and previous) on the General Help forum. For the most part (and most of the flavours) 15.10 will just be status quo with a  few caveats. I  dunno .. maybe even some new background art to keep us interested.

@matt

So you are saying definitively that there will be no "Snappy Personal" iso or  desktop for that matter?

Regards..

---

### Post by craig10x on 2015-06-14
@ventrical: From the links it sounds to me that they are saying that indeed snappy will be coming into the isos...it's just that it will continue to be called ubuntu next...and that he got it running on 32 bit fine but just needed to work out and get it going properly for 64 bit...

Also, the plan is to have two versions (for the forseeable future)  ubuntu with deb and ubuntu with snappy when 16.04 is released...that is what they meant when they said the deb version isn't going away anytime soon...

---

### Post by ventrical on 2015-06-14
> **craig10x said:**
> @ventrical: From the links it sounds to me that they are saying that indeed snappy will be coming into the isos...it's just that it will continue to be called ubuntu next...and that he got it running on 32 bit fine but just needed to work out and get it going properly for 64 bit...

Also, the plan is to have two versions (for the forseeable future)  ubuntu with deb and ubuntu with snappy when 16.04 is released...that is what they meant when they said the deb version isn't going away anytime soon...

Fair enough. I am in wait and see mode. However it pans out I plan to work with it, to get it working , to break it, bust it , fix it and then bust it again :) I am certain that whatever  come downs the pipe it will brand the same ubuntu performance and high quality we've seen for the past 5 years.

Regards..

---

### Post by mc4man on 2015-06-14
I'm likely misunderstanding their intention but i'd think that 'snappy apps' (after the fact of an install) are apps like any from any app store
(- ie. no source binaries that are free or pay for. Whether Ubuntu will allow free with adverts no idea.
Sort of like what's around now as click - [https://uappexplorer.com/apps](https://uappexplorer.com/apps)

As far as the 46k packages currently available for the Desktop install I'd think for the most part they'd stay that way (.deb

If in fact Ubuntu on the Desktop is eventually going to be app store only (apps, web apps, cloud apps ect.),  I'm sure some would be quite satisfied & some not interested in the least.

---

### Post by grahammechanical on 2015-06-24
email date: Friday June 19th

> work continued on the _snappy personal image_, the image builder and
channel are working fine, the tools are being updated to support [U]the new
channel[/U] and the image is close from successful boot to a lightdm greeter

[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-June/004669.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-June/004669.html)

> <Laney> &#8226; some chats about snappy desktop thing, set up release team so seb128 can do his own builds :-)

> <seb128> &#8226; spent a good part of the week fighting with snappy & personnal image build, we are getting there (got an image to build but it's not booting now)

[http://ubottu.com/meetingology/logs/ubuntu-desktop/2015/ubuntu-desktop.2015-06-16-15.31.log.html](http://ubottu.com/meetingology/logs/ubuntu-desktop/2015/ubuntu-desktop.2015-06-16-15.31.log.html)

---

### Post by pixelro on 2015-06-24
ubuntu-device-flash -h

Available commands:
  core      Creates ubuntu core images
  personal  Creates ubuntu personal images
  query     Run queries against the image server
  touch     Flashes ubuntu touch images

---

### Post by cariboo on 2015-06-24
> **pixelro said:**
> ubuntu-device-flash -h

Available commands:
  core      Creates ubuntu core images
  personal  Creates ubuntu personal images
  query     Run queries against the image server
  touch     Flashes ubuntu touch images

That command is meant to flash handheld devices, and won't do much good when used on desktop, or laptop systems. I have my doubts about how well the command works on all hand held devices, I know for sure that it won't work on my RCA 7" tablet.

---

### Post by ventrical on 2015-07-09
Bump!

---

### Post by grahammechanical on 2015-07-12
Remember when we installed snappy personal in kvm? Apart from installing qemu-kvm we also

1) installed ubunt-device-flash
2) we ran this command

```
sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
```

That downloaded the file personal_x86.img in the home folder which you showed can be used by Disks utility to restore the image to USB stick. I have just run that command again and it downloads the latest personal-x86.img file - version 35 compared to version 32 when I first run the command a few days ago.

So, we now have a choice. Update the existing install on USB stick or download a later version and restore the image using Disks utility. Anyway, the images are being updated.

Regards.

---

### Post by pixelro on 2015-07-12
> **grahammechanical said:**
> Remember when we installed snappy personal in kvm? Apart from installing qemu-kvm we also

1) installed ubunt-device-flash
2) we ran this command

```
sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
```

That downloaded the file personal_x86.img in the home folder which you showed can be used by Disks utility to restore the image to USB stick. I have just run that command again and it downloads the latest personal-x86.img file - version 35 compared to version 32 when I first run the command a few days ago.

So, we now have a choice. Update the existing install on USB stick or download a later version and restore the image using Disks utility. Anyway, the images are being updated.

Regards.

[https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/](https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/)

---

### Post by ventrical on 2015-07-13
> **grahammechanical said:**
> Remember when we installed snappy personal in kvm? Apart from installing qemu-kvm we also

1) installed ubunt-device-flash
2) we ran this command

```
sudo ubuntu-device-flash personal rolling --channel edge -o personal_x86.img --developer-mode
```

That downloaded the file personal_x86.img in the home folder which you showed can be used by Disks utility to restore the image to USB stick. I have just run that command again and it downloads the latest personal-x86.img file - version 35 compared to version 32 when I first run the command a few days ago.

So, we now have a choice. Update the existing install on USB stick or download a later version and restore the image using Disks utility. Anyway, the images are being updated.

Regards.

@graham..

 Thanks for looking into that.

regards..

---

### Post by ventrical on 2015-07-13
> **pixelro said:**
> [https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/](https://system-image.ubuntu.com/ubuntu-personal/rolling/edge/)

The current image file is only 376 KBs ??

---

### Post by ventrical on 2015-07-19
> **cariboo said:**
> That command is meant to flash handheld devices, and won't do much good when used on desktop, or laptop systems. I have my doubts about how well the command works on all hand held devices, I know for sure that it won't work on my RCA 7" tablet.

For x86 architecture it works as in amd64 branded desktops. it will run the current version of unity8. My RCA? Haven't had time to do much on those. 

Regards..

---

### Post by ventrical on 2015-09-16
Since we have a lot of chat about snappy here I am just making mention that I am going to try to back-step a bit over to the snappy-core spin and see if I can get that going to a working desk-thing. Hew ... there it is .. the new IoT is not a desk-top .. it is a desk-thing:)

@Cariboo

Is your RCA 7 still bricked? I have 2 of those and want to get rolling   with them. Big problem here is that I cannot get a reliable *root* app without some other nonsense comming along with it, usually preventing the image from be loaded onto the firmware-drive.

regards..

---

### Post by cariboo on 2015-09-16
> **ventrical said:**
> Since we have a lot of chat about snappy here I am just making mention that I am going to try to back-step a bit over to the snappy-core spin and see if I can get that going to a working desk-thing. Hew ... there it is .. the new IoT is not a desk-top .. it is a desk-thing:)

@Cariboo

Is your RCA 7 still bricked? I have 2 of those and want to get rolling   with them. Big problem here is that I cannot get a reliable *root* app without some other nonsense comming along with it, usually preventing the image from be loaded onto the firmware-drive.

regards..

My RCA tablet was bricked, but I found a way to make it usable again by using the instructions in this thread:

[http://forum.xda-developers.com/general/general/stock-rom-twrp-root-oc-uv-rca-7-voyager-t3087075](http://forum.xda-developers.com/general/general/stock-rom-twrp-root-oc-uv-rca-7-voyager-t3087075)

The tablet is semi usable, as I only use it as an ebook reader. I think the image that is provided in that thread is not the same as the original, as if I try try to do anything else it frequently locks up. I have another image, but I haven't tried it yet to see if it solves the problems I'm running into.

---

### Post by QDR06VV9 on 2015-09-16
Been using this  TWRP: [SuperSu]("http://forum.xda-developers.com/showthread.php?t=1538053")
on 2 Devices Samsung Tab2 && Sero7 Pro.<(Witch is more like Nexus7 Tab)
Works Well for my needs.
Just to be clear No Snappy's will work on either Devise.

---

### Post by ventrical on 2015-09-16
@cariboo,runrickus,

thanks...

regards..

er.. if I get ANYTHING on these tablets I have made it a priority to post in this thread

---

### Post by QDR06VV9 on 2015-09-16
> **ventrical said:**
> @cariboo,runrickus,

thanks...

regards..

er.. if I get ANYTHING on these tablets I have made it a priority to post in this thread
That is great will watch this thread.

---

### Post by ventrical on 2015-09-16
I got this sort of ... ummm  block at the moment. There is only one program that will #root# my slates and it installs this little horse icon  which is some sort of malware or adware or whatever  it is... but I am committed .. so I will find a way.

Regards

---

### Post by ventrical on 2015-09-16
Here are desktop-next preinstalled current images.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-preinstalled/current/)

---

### Post by pixelro on 2015-09-17
[COLOR=#000000][FONT=Ubuntu]The preinstalled-desktop-next filesystem archive allows you to unpack a preinstalled version of Ubuntu-Desktop-Next onto a target device.

how do you do that?[/FONT][/COLOR]

---

### Post by ventrical on 2015-09-17
> **pixelro said:**
> [COLOR=#000000][FONT=Ubuntu]The preinstalled-desktop-next filesystem archive allows you to unpack a preinstalled version of Ubuntu-Desktop-Next onto a target device.

how do you do that?[/FONT][/COLOR]

I am working on it. The first trick is that you have to #root# your device. I was finally able to download an app from the Google App Store called Kingo Root. Then you should read this  thread: [http://ubuntuforums.org/showthread.php?t=2254725](http://ubuntuforums.org/showthread.php?t=2254725)

There is a lot of info there on what we tried to do.  I do not guarentee it will work.

Regards..

#note#  With Kingo Root from Google app Store you have to  yes, yes, yes to all the windwos that pop up .. then /update/ yes/next and it will bring up browser ... download again from browser and open .. then it should #root# your device if you do not already have it rooted.

---

### Post by cariboo on 2015-09-17
My tablet was rooted, so I went looking for a way to make it at least functional. I found a solution [here]("http://forum.xda-developers.com/general/general/stock-rom-twrp-root-oc-uv-rca-7-voyager-t3087075"). The process got me think that maybe that maybe the flash tool linked to, in the thread maybe the way to go. The tool sees the device as an M8127 smart phone. If we could find an image that would work with that device there may be some hope.

---

### Post by ventrical on 2015-09-17
So we have to use a Windows OS.  Fair enough.

---

### Post by QDR06VV9 on 2015-09-17
Huumm? I already have TWRP maybe i will try this on the Sero7 Pro.
It is susposed to be like the Nexus 7.
Naa, need to do alittle more research first. Just seems to be the wiser thing to do first. As I can be a little Wild in these matters.:D
Thanks for keeping this thread updated Guys I Apperciate your input here.


Regards

---

### Post by ventrical on 2015-09-18
> **cariboo said:**
> My tablet was rooted, so I went looking for a way to make it at least functional. I found a solution [here]("http://forum.xda-developers.com/general/general/stock-rom-twrp-root-oc-uv-rca-7-voyager-t3087075"). The process got me think that maybe that maybe the flash tool linked to, in the thread maybe the way to go. The tool sees the device as an M8127 smart phone. If we could find an image that would work with that device there may be some hope.

I have:

```

If       lcm=[COLOR=Magenta]cpt_clap070wp03xg_lvds[/COLOR]      < you need to use v31 files

```

so I will need v31 files.

---

### Post by ventrical on 2015-09-18
Can't get 'scatter-file' to come up in dialog box. Had a nice 2 hour flashback session witn Windows 7. It decided to tell me that my install was not Genuine and that it was Counterfeit.  Once thing for sure is that I can always depend on MicroSoft to insult  my computer :) And the pop-ups .. ??? Worse now that ever.

Thank you ubuntu for giving me simplicity.

I do have another 'authentic' box in the closet. I keep it updated for rare occasions like this. :)

regards..

---

### Post by ventrical on 2015-09-18
There is this other tool  (google apps)that allows to configure images to sd card and be able to boot from there. I'll check it out. If I can run LXDE 15.10 in VNC I certainly can get android slate to dual boot.

regards..

---

