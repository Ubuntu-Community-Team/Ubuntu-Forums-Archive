---
title: "when will unity 8 be usable"
date: 2016-07-16
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2016-07-16
i have tried to install unity 8 and when i use nouveau driver it doesn't work when i get it to finally boot it is really slow and unusable. i know that it is still very early stages of development and expect problems, but i have seen a few youtube videos and wanted to try it. 
or when i try nvidia driver it just keeps bouncing at the login screen. 

i used the 
```
sudo apt-get install unity8-desktop-session-mir
```

logged out and back in using the new session.

---

### Post by grahammechanical on 2016-07-16
When will it be usable? Your guess is as good as mine. I get a frozen desktop without Unity app indicators or launcher and a mouse pointer frozen in the centre of the screen. And that is an improvement to the black screen I was getting 18 months ago. 

The developers talk of there being a 16.10 ISO image that installs Unity 8 as an alternative to Unity 7 as part of the installation process. When that ISO image is released I will test the daily built images and I expect that I will be reporting that Unity 8 session is broken again and again.

Regards.

Edit: From the post by Doug S I realize that my comment needed some clarification. Replace "Unity 8 as an alternative to Unity 7" with "Unity 8 as an alternative login session to Unity 7" as part of the install process. In other words we will not need to install Unity 8 to get a Unity 8 alternative session and the target is the release date of Ubuntu 16.10.

---

### Post by Doug S on 2016-07-17
> **grahammechanical said:**
> The developers talk of there being a 16.10 ISO image that installs Unity 8 as an alternative to Unity 7 as part of the installation process.We (the doc team) were led to believe it would be an alternative login to the standard. A quote from [here]("https://lists.ubuntu.com/archives/ubuntu-doc/2016-June/020034.html"):

> One of the big things that should be coming up for 16.10 is that we want to ship Unity 8 as a (non-default) alternative
login shell alongside Unity 7.

I do have it sort of working on my one 16.10 LapTop computer (most of my computers are on 16.04).

---

### Post by ventrical on 2016-07-19
I have had very , very good success with unity8+libertine containers up until last week. Now, the libertine containers most always fail, even on high-end intel graphics. What we had there was a "preview" emphasis on the word "preview". I still have it working very well with it's standard browser, etc.. but it lacks any real effervescence  without libertine and x11apps working properly.

  I am assuming, however, that  development will accelerate  very quickly as Canonical has a large team committed to just unity8 desktop project (about 90 devs).

So the problems currently are to get libertine to work effectively and reliably and also get nVidia-graphics adapter drivers patched in on slightly older machines.

Regards..

---

### Post by grahammechanical on 2016-07-19
I have just been reading an Insights Ubuntu post about OTA 12. As the phone/tablet is using Unity 8 the information is indirectly related to Unity 8 on the desktop.

> We have introduced a smart new solution to allow access to the many more  desktop applications residing in the Ubuntu archive. Conventional  Debian packages will also work. This solution uses the Command Line  Interface to access the archive however using the Store interface to  directly install a full range of desktop apps will soon be available.  For an in-depth technical explanation of this process,

[http://insights.ubuntu.com/2016/07/19/over-the-air-12-go-big-wirelessly-connect-your-tablet/](http://insights.ubuntu.com/2016/07/19/over-the-air-12-go-big-wirelessly-connect-your-tablet/)

Then there is a link to this page

[http://kylenubuntu.blogspot.co.uk/2016/07/running-x-apps-on-ubuntu-devices.html](http://kylenubuntu.blogspot.co.uk/2016/07/running-x-apps-on-ubuntu-devices.html)

> currently the containers must be of the same Ubuntu series as the device: Vivid.

Perhaps I should put vivid in an LXC and then install Unity 8 session in the container?  Better yet, I will cross over into the parallel universe whre Canonical has already solved all these issues. 

Oh! In this universe Skynet is a snap app running on Ubuntu Open Stack cloud and no one can hack it to shut it down.

Regards.

---

### Post by terry_gardener on 2016-07-19
is it better to install from the ppa or direct from official 16.10 repos

---

### Post by mc4man on 2016-07-20
> **terry_gardener said:**
> is it better to install from the ppa or direct from official 16.10 repos
Until there is a working libertine I think you're wasting your time trying unity8 in 16.10. 
Here with Intel the unity8 session loads fine in 16.10 but there is almost nothing to do. - 
A working web browser
A working system settings
A working ubuntu store with a handful of apps, none work.
That's it.

As far as libertine - currently broken, [containers can't be created]("https://bugs.launchpad.net/libertine/+bug/1598785"). Supposedly fixed in next libertine release though likely not the end of current issues.
The mentioned ppa has nothing for 16.10 anyway. You'd be better of trying 8 in 16.04 though it's possible your hardware has poor support.

---

### Post by ventrical on 2016-07-21
@mac4man

+1

 Libertine is now the gem of the unity8 desktop. It is the 'next' shiny new thing :) I had it working great but now all instances across the board are broken. After all .. it was a preview.

Will keep watching.

Regards..

---

### Post by ventrical on 2016-07-25
> **mc4man said:**
> Until there is a working libertine I think you're wasting your time trying unity8 in 16.10. 


Just an update. unty8 working with nVidia and intel. (16.04-16.10)
Libertine not working even with new python3-libertine updates and other new upgrades to that package.

regards..

---

### Post by ventrical on 2016-07-25
> **terry_gardener said:**
> i have tried to install unity 8 and when i use nouveau driver it doesn't work when i get it to finally boot it is really slow and unusable. i know that it is still very early stages of development and expect problems, but i have seen a few youtube videos and wanted to try it. 
or when i try nvidia driver it just keeps bouncing at the login screen. 

i used the 
```
sudo apt-get install unity8-desktop-session-mir
```

logged out and back in using the new session.

You need to drop the 'mir' and use the ppa for now.

Here are updated instructions from mHall.

[http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)

---

### Post by mc4man on 2016-07-25
> **ventrical said:**
> Just an update. unty8 working with nVidia and intel. (16.04-16.10)
Libertine not working even with new python3-libertine updates and other new upgrades to that package.

regards..
I had tried the newer libertine here prior to it releasing (16.10). While it then allowed creating a container it crashed on trying to install into. 
As far as 16.04 there aren't any new packages, maybe in that ppa? (haven't checked
One issue with that ppa in 16.04 - if one does a full upgrade with it enabled & then tries to go back to normal (ppa-purge) it can be a chore to set things straight as ppa-purge cannot do the job completely.

---

### Post by grahammechanical on 2016-07-25
I have not seen any updates that are likely to change the Unity 8 situation on my machine. So, I will wait a few hours/days to see what comes down the pipe. But I have installed Libertine. I had this crazy idea that I could use Libertine to load applications in a container on Unity 7. I miscalculated. Libertine is designed to put an application icon into a Unity 8 scope and not into the Unity 7 Dash. I see no icon to launch the application in the container.

I got an update to libertine the other day and now I get a system error message about libertine when I load into Unity 7. Such is life. Worse things happen at sea. As my granny used to say.

Regards.

---

### Post by mc4man on 2016-07-25
I think it may be more topical to think - when will unity8 be testable?, usable doesn't seem realistic till next yr. at best

---

### Post by terry_gardener on 2016-07-25
> **mc4man said:**
> I think it may be more topical to think - when will unity8 be testable?, usable doesn't seem realistic till next yr. at best

i just wanted to test it as some off the youtube videos look decent and i wanted to test it to see what it is like for myself. 
just at the moment it doesn't even load at all for me anyway and since they have being saying for years that it will be ready for the next release i thought it would at least load by now and be able to test it. 

i know that it is a massive project and it is going to take time to get it right but seems like the phone/tablet is well ahead of the desktop version even though the user base for ubuntu mobile devices it probably substantially less than the desktop.

---

### Post by ventrical on 2016-07-25
> **grahammechanical said:**
> I have not seen any updates that are likely to change the Unity 8 situation on my machine. So, I will wait a few hours/days to see what comes down the pipe. But I have installed Libertine. I had this crazy idea that I could use Libertine to load applications in a container on Unity 7. I miscalculated. Libertine is designed to put an application icon into a Unity 8 scope and not into the Unity 7 Dash. I see no icon to launch the application in the container.

I got an update to libertine the other day and now I get a system error message about libertine when I load into Unity 7. Such is life. Worse things happen at sea. As my granny used to say.

Regards.

" There was a famous Englishman who once said: 'We must all do out duty when they wave the flags for England' " my grandpa used to say.

Regards..

---

### Post by ventrical on 2016-07-26
> **terry_gardener said:**
> i just wanted to test it as some off the youtube videos look decent and i wanted to test it to see what it is like for myself. 
just at the moment it doesn't even load at all for me anyway and since they have being saying for years that it will be ready for the next release i thought it would at least load by now and be able to test it. 

i know that it is a massive project and it is going to take time to get it right but seems like the phone/tablet is well ahead of the desktop version even though the user base for ubuntu mobile devices it probably substantially less than the desktop.

It was working really well there for a while  and all of a sudden it went belly up. This is to be expected in development.  I am optimistic that  there will be an intense run of upgrades through August.

Just keep updating your install.

Regards..

---

### Post by ventrical on 2016-07-27
> **mc4man said:**
> I had tried the newer libertine here prior to it releasing (16.10). While it then allowed creating a container it crashed on trying to install into. 
As far as 16.04 there aren't any new packages, maybe in that ppa? (haven't checked
One issue with that ppa in 16.04 - if one does a full upgrade with it enabled & then tries to go back to normal (ppa-purge) it can be a chore to set things straight as ppa-purge cannot do the job completely.

Just got this:

[SIZE=2]* Changed in: libertine/trunk
       Status: Fix Committed => Fix Released

** Changed in: libertine/devel
       Status: Fix Committed => Fix Released

for this bug 
[https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1596020)

So maybe libertine is fixed now ?


[/SIZE]

---

### Post by ventrical on 2016-07-27
Yep .. fixed and green for testing. It is working even sleeker than before!

Regards..

Thank-you Chris Townsend and team for  making this happen! :)

---

### Post by ventrical on 2016-07-27
I am trying out different deb packages. I am having a riot . . I installed htop just to take a peek under the hood and it almost brought me to tears .. to see the development taking off like  a rocket !. Certainly appears that Cannonical devs are determined to make unity8+libertine default come October. This is not a sprint .. this is a marathon.

Regards..

---

### Post by mc4man on 2016-07-27
> **ventrical said:**
> Yep .. fixed and green for testing. It is working even sleeker than before!

Regards..

Thank-you Chris Townsend and team for  making this happen! :)

Doesn't work at all on a newish install nor on a fresh install of todays image. 2 - 3 crashes, no way to create a container.
main crash - [https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1606505](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1606505)
(- they say the crash is noise, well then it (libertine) just doesn't work. 

(- another odd thing noticed on fresh install. Installing the libertine scope doesn't actually enable the scope. It seems the libertine package is also needed. If in fact that's  the case then it should be a dep or recommend of the scope.

---

### Post by ventrical on 2016-07-27
> **mc4man said:**
> Doesn't work at all on a newish install nor on a fresh install of todays image. 2 - 3 crashes, no way to create a container.
main crash - [https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1606505](https://bugs.launchpad.net/ubuntu/+source/libertine/+bug/1606505)
(- they say the crash is noise, well then it (libertine) just doesn't work. 

(- another odd thing noticed on fresh install. Installing the libertine scope doesn't actually enable the scope. It seems the libertine package is also needed. If in fact that's  the case then it should be a dep or recommend of the scope.

In my case the containers are being created in the background after the bug I reported was fixed/released.  Then I log off/log on, open libertine and there are containers ready for apps. it's still running as I type this message. This on a nVidia machine I reported a bug on on this machine:

---

### Post by mc4man on 2016-07-27
On the fresh install this is all I get as seen in screenshot.
Clicking on libertine opens a dialog box about configuring, clicking the button opens another dialog where the container is named & password.  (it may very well create the container.
But nothing ever changes in  Scopes so no way to install, in other words it always looks like the screenshot

---

### Post by ventrical on 2016-07-27
Xenial installs are a no go.

 I am not sure what I did to get mine working. Maybe it is just a freak or something.

I did,

```

sudo apt-get update
sudo apt-get dist-upgrade

```

while in ubuntu-desktop gnome-terminal.

 I restarted (soft) then logged into unity8. I opened up libertine and created a container. I originally got the bounce back  "install" screen but I could see my modem lights going. After activity was over I logged off and then logged back on and there was the created container. I then clicked the  add apps + sign and installed firefox and nautilus.

 The only caveat I can think of is that I did not have the terminal.click installed. I installed the terminal.click after I was able to get Desktop Apps working. I doubt this had anything to do with it. Who knows ? I plan to keep at it.  I am not going to update the one install I have working. I want to push it to breakage adn then see what happens from there.

 Just asking . Is there anyway installing the terminal.click prior to creating container may have an  effect on libertine overall.?

Regards..

---

### Post by mc4man on 2016-07-27
Well made a little progress no thanks to an inane default design.
The default Scopes window is very small & you can scroll down. When you do scroll down (only fully exposes the useless ubuntu store) the ^ icon disappears. So I assumed the ^ only exposed the same as scrolling. 
However it doesn't, it opens some manager type screen 

In there was the Desktop apps > nothing. After a few log out/in Vim appeared but useless as it never finishes loading.
Also see no means to install deb packages to a container, there is no apparent libertine manager & the libertine icon/scope just creates containers (see I ended up creating 4 currently empty ones

So dead end, maybe I'm missing something, maybe it's just not working..

---

### Post by ventrical on 2016-07-28
Up all night. Testing yakkety fresh installs on highend Intel. Libertine just not working.

---

### Post by terry_gardener on 2016-07-28
just tried it again and get the same problem get black screen after nouveau messages. 

nouveau 0000:01:00.0: fifo read fault at 0000011000 engine 07 .....
nouvaeu 0000:01:00.0: fifo: fifo engine fault channel 2, recovering
nouvaeu 0000:01:00.0: unity-system-co:failed to idle channel 2

i have the nvidia gtx960 card 

i guess i will have to be patient.

---

### Post by terry_gardener on 2016-07-28
i think i have figured it out, when i checked the dmesg and it is not loading the nvidia firmware for my card and when i checked into this the nvidia 900 series cards uses digitally signed firmwares for there newer cards. 

 0.736329] nouveau 0000:01:00.0: Direct firmware load for nvidia/gm206/fecs_inst.bin failed with error -2
[    0.736331] nouveau 0000:01:00.0: gr: failed to load fecs_inst

so looks like i will have to wait for the drivers from nvidia to work with mir/unity 8.

---

### Post by ventrical on 2016-09-01
> **terry_gardener said:**
> is it better to install from the ppa or direct from official 16.10 repos

I have done a fresh install of yakkety and  unity8-desktop-session , libertine and libertine-scope are now in the repos.  I have a working install with the libertine but there are still GUI bugs and the Ubuntu store is useless ATM.

...so better now to test without PPA.

Regards..

---

