---
title: "Hydrogen no longer plays in Karmic"
date: 2009-10-30
forum: Ubuntu Studio
---

### Post by zaarin on 2009-10-30
So I just upgraded to Karmic.  There are lots of things that no longer work.  I am trying to just deal with it, but there is one thing that I really miss:

Hydrogen drum machine.

It no longer plays.  The program loads up and appears on screen normally, and everything looks appropriate on screen, but when I click play, nothing happens.  Literally nothing at all.  It says "Playing" in the information bar on the bottom left, but it doesn't play at all.  No sound, the track slider doesn't move across, nothing.  It just sits there.  Any ideas?  Heard of anything?

---

### Post by sgx on 2009-10-31
> **zaarin said:**
> So I just upgraded to Karmic.  There are lots of things that no longer work.  I am trying to just deal with it, but there is one thing that I really miss:

Hydrogen drum machine.

It no longer plays.  The program loads up and appears on screen normally, and everything looks appropriate on screen, but when I click play, nothing happens.  Literally nothing at all.  It says "Playing" in the information bar on the bottom left, but it doesn't play at all.  No sound, the track slider doesn't move across, nothing.  It just sits there.  Any ideas?  Heard of anything?
Do you have the everything you need in both

/home/user/.hydrogen    and
/usr/share/hydrogen?

Projects, songs, kits?

Is the project you have loaded match the kit you have loaded?

Have you manually checked that the soundcard you want is the one being used? Is Hydro manually connected to alsa with qjackctl?

Did you do a clean full install of Karmic?

Did you lock out the networking, wireless, webcam yet etc 

Its a new OS, could be lots of gremlins lurking ;)

---

### Post by zaarin on 2009-10-31
I did not do a full clean install of Karmic because I didn't want to have to reconfigure and redownload everything I have set up thus far since... Gutsy.  That would be a lot of downloading and reconfiguring.  So far I haven't had this many problems with any of the other releases.  Honestly, I am not willing to start everything from square one all over again just to get Hydrogen working.  That would be too much.  I will figure out another solution if it comes to that.

I haven't locked out anything (network, webcam, etc) because... frankly, I'm kind of a noob and don't even know what you mean.  :oops::oops::oops:

As far as Hydrogen itself goes, I am sure that the problem is with Karmic (or my own retarded self) and not with Hydrogen because I did a fresh clean reinstall of Hydrogen and made a clean, fresh new song from scratch, and that wouldn't play either.

---

### Post by knattlhuber on 2009-12-04
I installed Hydrogen on a fresh Karmic install and had exactly the same problem. After setting the Audio Driver in the preferences to ALSA, I got sound. However, the speed of the rhythm changed ad lib when I played the demos. I guess it only works well with the RT kernel.

---

### Post by sgx on 2009-12-05
> **zaarin said:**
> I did not do a full clean install of Karmic because I didn't want to have to reconfigure and redownload everything I have set up thus far since... Gutsy.  That would be a lot of downloading and reconfiguring.  So far I haven't had this many problems with any of the other releases.  Honestly, I am not willing to start everything from square one all over again just to get Hydrogen working.  That would be too much.  I will figure out another solution if it comes to that.

I haven't locked out anything (network, webcam, etc) because... frankly, I'm kind of a noob and don't even know what you mean.  :oops::oops::oops:

As far as Hydrogen itself goes, I am sure that the problem is with Karmic (or my own retarded self) and not with Hydrogen because I did a fresh clean reinstall of Hydrogen and made a clean, fresh new song from scratch, and that wouldn't play either.
I hope at some point you will do a fresh install with a separate /home parition, so when yo must or want to reinstall, your private settings 
and data are untouched (you must specify not to reformat /home in the reinstall dialogue/setup. 
I find the Mandriva/pclinuxos installer the easiest to use for resizing or setting up partitons. You can powerdown the system once it has done the formatting, before it begins installing anything. Then reboot with your desired install media. You can of course throw a cheap/used hardisk in a $20 usb drive enclosure, and enjoy extra distros booting from that, leaving karmic the way you want it.
Cheers

---

### Post by markbuntu on 2009-12-08
Did you check in File/Preferences/Audio System?
You may need to change auto to something else to get it to work, like jack if you are using jack, or alsa if you are not

---

### Post by DerickX on 2009-12-09
Set Hydrogen to use JACK. Make sure your system is configured well to use JACK. Use Hydrogen 0.9.4

---

