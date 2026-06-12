---
title: "Can't enter Unity8/Mir session (live USB)"
date: 2016-01-30
forum: Ubuntu Development Version
---

### Post by adam-p on 2016-01-30
Is there a fundamental reason that unity8-desktop-session-mir won't work on a live USB of the latest 16.04 image (2016-01-28/29)? I tried (but was not necessarily systematic with) attempting a -rw remount, enabling of -proposed, installation of the -dev mir mesa graphics tools, and a couple of other things, but the failure seems pretty persistent. 
[B]

_From [Bug #1539811]("https://bugs.launchpad.net/ubuntu/+source/unity8-desktop-session/+bug/1539811")_[/B]_:_

This is a live USB environment (16.04, 2016-01-29 image). HP Envy x360 hybrid notebook. Package installed: 1.0.12+15.10.20150609-0ubuntu1 .
 After installing the mir desktop session package and choosing  "logout", the greeter correctly shows Unity8 as a login option. After  entering "ubuntu" and a blank password, the screen goes to black (with  backight), the fan runs for a few seconds of high activity, and no  graphical session ever actually starts.  The other tty screens remain  available, and lightdm is eventually able to restart (though only after  some time, and it is unclear if the commands to restart it are actually  helping).

**   Some selected error messages from the Unity8/Mir session login attempt:**

*   From lightdm.log:*
[+158.12s] DEBUG: Session pid=6899: Greeter requests session unity8-mir
[+158.12s] CRITICAL: g_dbus_connection_call_sync_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed

*  From unity-system-compositor.log:*
dm_connection_start
ERROR: Throw location unknown (consider using BOOST_THROW_EXCEPTION)
Dynamic exception type: boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<boost::system::system_error> >
std::exception::what: write: Broken pipe
...
Closing session GDK-Mir
ERROR: /build/mir-UeyFew/mir-0.19.0+16.04.20160128/src/common/fatal/fatal.cpp(55): Throw in function void mir::fatal_error_except(const char*, ...)
Dynamic exception type: boost::exception_detail::clone_impl<boost::exception_detail::error_info_injector<std::runtime_error> >
std::exception::what: Couldn't clear output eDP-1 (drmModeSetCrtc = -13)

*   From syslog:*
Jan 29 22:40:41 ubuntu org.freedesktop.Notifications[7323]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Jan 29 22:40:41 ubuntu org.freedesktop.Notifications[7323]: Unable to init server: Could not connect: Connection refused
Jan 29 22:40:41 ubuntu org.freedesktop.Notifications[7323]: (notify-osd:7672): Gtk-WARNING **: cannot open display:
Jan 29 22:40:42 ubuntu dbus[1325]: [system] Activating service name='com.canonical.SystemImage' (using servicehelper)
Jan 29 22:40:42 ubuntu com.canonical.SystemImage[1325]: usage: system-image-dbus [-h] [--version] [-C DIRECTORY] [-v]
Jan 29 22:40:42 ubuntu com.canonical.SystemImage[1325]: system-image-dbus: error:
Jan 29 22:40:42 ubuntu com.canonical.SystemImage[1325]: Configuration directory not found: .load() requires a directory: /etc/system-image/config.d
Jan 29 22:40:42 ubuntu dbus[1325]: [system] Activated service 'com.canonical.SystemImage' failed: Launcher could not run (out of memory)

 The *Unity8.log* and *Unity8-dash.log* files are just repetitions of:
QXcbConnection: Could not connect to display .

---

### Post by grahammechanical on 2016-01-30
I would not say that is a problem with the live session. As far I as I am concerned it is a basic problem with unity8-desktop-session-mir itself. I have never tried it on a live session. Why would it work on a live session when it does not work on an installed session?

I does not matter if I use open source or proprietary video drivers the thing will either give login screen bounce or never get to a login screen once the switch is made to Mir. And that situation has been consistent from 14.04 until now.

Mind you, the core apps that are installed at the same time will appear in the Dash and load in Unity 7. 

I have some hopes for the intention that click apps should be installable on 16.04 + Unity 7. But not very great hopes. Updating today a xenial with unity8 brought in unity-scope-click but I could not see it having any effect. And it is not installed in my xenial that does not have unity8. Although click-ubuntu-policy is installed.

Perhaps Gnome Store will install (in future) click apps. Or may be they will install through the Dash. I do have Gnome Store installed through a PPA. That too has a way to go. At lot has to happen in the second half of the development cycle. 

Excitement or Disappointment. Which will it be?

Oh, by the way. Why a blank password? It should be your normal user password.

Regards.

---

### Post by adam-p on 2016-01-30
> **grahammechanical said:**
> I would not say that is a problem with the live session....Why would it work on a live session when it does not work on an installed session?

I don't quite understand. Are you saying that this package is fundamentally broken / isn't maintained and fails to work on many kinds of hardware? I didn't get that impression from the repository. Are the error messages that you get in your logs when you try to use it similar to the ones I'm seeing?

> **grahammechanical said:**
> 
Oh, by the way. Why a blank password? It should be your normal user password.
Regards.

Why would a live USB running the a daily Xenial image have my user account on it?

---

### Post by ventrical on 2016-01-30
I do not know if this will help but I emailed Daniel Holbach and inquired of him about snappy personal (which is unity8+mir on snappy_core and he replied that he is only working with snappy and Snapcraft so I e-mail Mark Shuttleworth directly asking:

> 

Hello Mark,

I am inquiring about the current state of  snappy_personal desktop images for x86/amd64 desktop devices. I , along  with a few others at Ubuntu Development Version Testing,  have been  early adopters trying to test the images on various desktop frameworks. Over a month ago the images stopped updating. They were  called  <personal_x86.img> which  had Unity8+mir on top of snappy_core. 

My  question is: Will there be more snappy_desktop_personal images coming  out in the near future or will we have to wait until the next cycle?

I  am current admin for Ubuntu Development  Version Testing and I would  like to share with other early adopters your take on this matter.

Thank you.

Regards..


 So if I get a reply I will put it up here. I have tried to inquire from other members of the team what is going on with this and it appears hard to get any distinct direction as to where this project is going. I just want to move on from 'waiting for snappy personal' and get to testing other flavours.

Regards..

---

### Post by adam-p on 2016-01-31
> **ventrical said:**
> ...inquired...about snappy personal....
So if I get a reply I will put it up here. I have tried to inquire from other members of the team what is going on with this and it appears hard to get any distinct direction as to where this project is going. I just want to move on from 'waiting for snappy personal' and get to testing other flavours.


Sorry, now I'm even more confused. What is the connection between this problem and Snappy?

---

### Post by grahammechanical on 2016-01-31
Yes, it is very confusing. It has been confusing us who you might call Canonical watchers. Have you ever heard of pocket desktop? On Ubuntu On Air I have heard Canonical engineers speak of Ubuntu pocket desktop. I too am confused. But I will try.

We have Ubuntu phone. It is Mir + Unity 8 + click packaging. Click packaging is said to be a development of Debian packaging. But things progress and Click has evolved into Snap packaging. I am using expressions spoken by Canonical engineers.

It seems that there are advantages to having a Snappy OS. And I have heard talk that Ubuntu phone will some day move from click packaging to snap packaging. So, we now have Snappy associated with Mir & Unity 8 and then we start to think of the visionary concept of Convergence.

The other month Ventrical & I were installing something called personal_x86.img. It was built on wily code. It was Mir + Unity 8 + phone desktop running on x86 CPU desktop machines and not ARM CPU mobile devices. When we switched to tty1 and logged in we got this message

> Welcome to snappy Ubuntu Desktop Next. A transactionally updated Ubuntu. This is a *highly* experimental image.

It was interesting. The partition layout was very different from what we should now call Traditional Ubuntu and the transactional updates really worked well. If an update to the system failed then the process rolled back to the previously working version of the OS. No broken OS because of an update failure. It did not use apt-get to update. Every time there was a new image build we went into tty1 and ran sudo snappy update and ubuntu-core was downloaded and installed.

The last update or build to personal_x86.img was 17 October. Why have they stopping building new images and building them on xenial code? Ventrical & I were hoping to follow this development through to the release of Ubuntu Personal (A.K.A. Snappy Ubuntu Personal).

It remains to be seen if the new Ubuntu tablet convergence device will be Ubuntu phone (Mir + Unity 8 + click packaging + desktop apps) Or Ubuntu phone (Mir + Unity 8 + snap packaging + desktop apps) Or Snappy Ubuntu desktop next. And will it be built on xenial code?

It certainly is confusing.

Regards.

---

### Post by adam-p on 2016-01-31
Maybe I should be clearer. My confusion is about why it seems like this thread is being hijacked as a place to raise various and sundry issues that don't have any direct relationship to the problem that the post was actually about.

I don't have any special expertise in Mir/Unity8/Snappy/Click structure or development. And I don't know the history of how the unity8-desktop-session-mir package has been maintained or the details of how it technically integrates with all of those larger components. So I have wanted to stay open-minded. Maybe your pre-existing problem loading the session was actually the same bug, and you have details/logs/reports to help illuminate it.  Maybe click app compatibility has something to do with how lightdm or dbus need to set a connection to a Mir session, and it just looked unrelated to me. Maybe the development of Snappy Personal is what ensures up-to-date code in Mir/Unity8 for launching desktop sessions generically, and you guys were trying to say that Canonical falling behind on this is why you suspect the unity8-desktop-session-mir package isn't working on my normal, non-snappy, live Xenial image? I'm really trying to give the benefit of the doubt here.

But if frustrations about Click packages and Snappy Personal development don't actually have anything to do with my Mir session failing to get a display connection and throwing those errors, then I have to ask you to please respect [Rule 8]("http://ubuntuforums.org/misc.php?do=showrules") and not steer the thread off topic.

---

### Post by ventrical on 2016-01-31
I put the new message in a forum already created. I was not meaning to hi-jack this thread as I thought it was topical.

Please then see: [http://ubuntuforums.org/showthread.php?t=2285518&page=2&p=13431970#post13431970](http://ubuntuforums.org/showthread.php?t=2285518&page=2&p=13431970#post13431970)

Regards..

---

### Post by bapoumba on 2016-01-31
Moved 2 posts out.

---

### Post by grahammechanical on 2016-01-31
> I don't quite understand. Are you saying that this package is  fundamentally broken / isn't maintained and fails to work on many kinds  of hardware? I didn't get that impression from the repository. Are the  error messages that you get in your logs when you try to use it similar  to the ones I'm seeing?

I thought that it was clear that I was saying it was exactly that. I do not believe that you are having this problem because you have installed unity8-desktop-session-mir on a live session. That was what you thought, did you not?

When using wily development release I was using Ubuntu Web Browser every day. It has become a useful web browser. But on xenial it does not matter how many upgrades the developers push out it is still crashing every time I try to load it. The fact that an application exists in a development installation does not mean it will work.

May be these things will be fixed by release day. But I am not holding my breath. Development priorities change. Timetables slip. I have no problem with this happening. The plan is now to have snap apps running in Linux containers in 16.04 Unity 7. Mark Shuttleworth was unable to demonstrate this at ScaleX the other week but he said it will be there in 16.04. If I could test that on xenial right now or during February or March I would be more confident of these plans coming to pass.

---

