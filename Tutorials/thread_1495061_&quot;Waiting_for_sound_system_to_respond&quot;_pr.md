---
title: "&quot;Waiting for sound system to respond&quot; problem, Ubuntu 10.04"
date: 2010-05-27
forum: Tutorials
---

### Post by WitchCraft on 2010-05-27
When you have Ubuntu 10.04, and you login as root, you cannot change the sound volume or settings with the sound applet in the gnome-panel.

The solution:

Go to System->Preferences -> Startup Applications

Make sure you're in the tab 'Startup programs' 
-> Click on 'Add'

Name: Pulseaudio daemon
Command:/usr/bin/pulseaudio
Comment: Start the sound daemon

Now logout, then login again

->Fixed

---

### Post by bapoumba on 2010-05-28
Tip that is :)

---

### Post by cariboo on 2010-06-07
> **WitchCraft said:**
> When you have Ubuntu 10.04, and you login as root, you cannot change the sound volume or settings with the sound applet in the gnome-panel.

The solution:

Go to System->Preferences -> Startup Applications

Make sure you're in the tab 'Startup programs' 
-> Click on 'Add'

Name: Pulseaudio daemon
Command:/usr/bin/pulseaudio
Comment: Start the sound daemon

Now logout, then login again

->Fixed

If you need sound when doing administrative tasks as root, you're doing something wrong.

---

### Post by Siddiq36 on 2010-06-23
thanks. this works for me nicely. its a great fix. thanks again. good luck

---

### Post by pasokon on 2010-06-30
I have the problem everyone else does but it occurs when I am logged in as a normal user. Also, adding my user name to the groups pulse, pulse r-t etc. does not work! 

My problems do not end here. I cannot open pavucontrol. I looked in other threads and can't find a good fix for this.

Help me, please!;)

---

### Post by anonymous_itop on 2010-08-21
thank you WitchCraft, it's really fixed.

---

### Post by Ubuk2008 on 2010-10-18
Unfortunately, this method did not help me. What helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone

---

### Post by mondechris on 2011-01-19
I had same problem in Ubuntu 10.10.
Deleted the .pulse directory and restarted.
Worked fine, thanks

---

### Post by mondechris on 2011-01-19
I had same problem in Ubuntu 10.10.
Deleted the .pulse directory and restarted.
Worked fine, thanks

---

### Post by BabyRabbit96 on 2011-01-29
I read this post and nothing will help me. No previous or present posts will help me get sound working. Headphones work great but the speakers absolutly refuse, seems, to work. PLEASE HELP!

---

### Post by rottenart on 2011-01-30
I would add that I have purged pulseaudio. However, when I try to delete the ".pulse" directory it simply reappears. It's very strange. I don't have a chance to reboot to see if it works because it reappears too quickly.

---

### Post by robot_chicken_parm on 2011-02-12
i too was having the same problem when loggong into my defaut user, and after trying a million different things i found this thread, and i am glad i did!  i too went into the home folder, viewed hidden files, and deleted ".pulse" and restarted.  the problem seems to be completely solved and the .pulse folder is back where it was before i deleted it.  thank you for the help.  thanks everybody.  i LOVE ubuntu...  had this been a Windows problem they likely would have tried to con us into buying something.

---

### Post by psihokiller4 on 2011-02-18
thanks I screw something in it too

and got that message that couldn't get repaired back

but as I deleted hardware wasn't as it should be so ( luckily I backed up files ) files that needed to be deleted were:

70c36bbaf3b9fb67504ec28b4ce2dc1c-default-sink
70c36bbaf3b9fb67504ec28b4ce2dc1c-default-source
70c36bbaf3b9fb67504ec28b4ce2dc1c-stream-volumes.tdb

other files were from equaliser and others I don't know this files reproduce itself again very fast so deleting this files isn't that bas I just think so not :)

if it helps anyone :)

thanks for helpers --> (delete .pulse)

---

### Post by psihokiller4 on 2011-02-18
> **rottenart said:**
> I would add that I have purged pulseaudio. However, when I try to delete the ".pulse" directory it simply reappears. It's very strange. I don't have a chance to reboot to see if it works because it reappears too quickly.

yes but not same files so if you screw anything up and delete that files as I did you loose data that screw things :)

---

### Post by aggarwaldhruv on 2011-03-17
worked fine for me thanks......

---

### Post by Julian Luna on 2011-03-18
Sorry dudes im using 10.10 but when I delete that folder it suddenly reappears. I purged pulseaudio, should I do something like "sudo apt-get uninstall pulseaudio"? Or what? I followed the "Decently removing pulse" guide but the folder still reappears. Thanks

---

### Post by mikebravo on 2011-03-19
Wow! From May 2010 to March 2011 and we are still having trouble with something as fundamental as sound. That problem fell on me out of the clear blue sky, (if you don't count doing updates as something that would screw up a supposedly bullet proof operating system). I could hear audio on You Tube one day and zip the next, plus my display kept going gray and would not respond to mouse clicks. I followed the suggestion to add to the startup programs as shown early in this seed but it did not work. Then I followed the suggestion to delete .pulse and things were back to normal after I got into Sound Preferences and redid the settings that had gone off into la-la land.  Mark one down for Ubuntu, mark one up for the Forums.

---

### Post by brian mcgee on 2011-03-21
Same issue. The trouble started after moving my home folder from a 10.04 box to a 10.10 install. Renaming ~/.pulse and rebooting worked for me. I suspect a reboot is not necessary, but I had to reboot anyway...

---

### Post by xile_ on 2011-03-24
Using Ubuntu 10.10

Purging/deleting the .pulse folder from my home directory did the job.

---

### Post by linux lov3r on 2011-03-25
> **Ubuk2008 said:**
> Unfortunately, this method did not help me. What helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone


thanks for the methods, it's resolve my problem :D

---

### Post by sancho panza on 2011-05-03
Thanks all!

---

### Post by thxq on 2011-05-14
:popcorn: cheers u get me the way to go


thanks a lot!!!

---

### Post by Vidhuran on 2011-06-19
Thanks all ...

Helped me fix the thing that was bugging me the whole day .:)

---

### Post by ooboontwo on 2011-06-24
I don't have a hidden .pulse folder in my Home directory. Sound works, but I have no sound icon in the panel. YES, I have the Indicator Applet attached to the panel and I see the envelope icon, but no sound icon.

I tried uninstalling and reinstalling pulseaudio but that didn't help the situation.

Ideas?

Cheers,
Cody

---

### Post by billrandle on 2011-06-26
Deleted the .pulse folder and the problem was fixed on re-boot.

---

### Post by Wejdan on 2011-07-04
> **Ubuk2008 said:**
> Unfortunately, this method did not help me. What helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone

Worked!! thx a lot :)

---

### Post by tpost001 on 2011-07-06
I am in Ubuntu 10.10.  Today a I did an Update, which included a kernel update.  So I had to reboot to complete the update.  Since then no sound.  Why did I have to update?  It worked flawlessly before.  I followed all the instructions in this thread.  The first time I deleted .pulse from my home directory and rebooted, the sound came back.  I was happy.  Then the sound did not work in SKYPE.  I deleted and reinstalled SKYPE through Synaptic.  Then the sound was even gone on the desktop and the little speaker Icon shows no status and when I click on the Sound Preferences I get "Waiting for sound system to respond."  Now every time I delete .pulse and reboot, the sound does not come back and I always get this message.  Is the .pulse folder suppose to be forever deleted, or by deleting it, it just restores a new copy hopefully with the correct settings?  I have gone back to my former kernel in GRUB and still no sound.  Its clobbered.  Any help please?

---

### Post by bpill on 2011-09-09
None of your tips worked for me.
Deleting .pulse did not do anything at all.

I still have an icon with a speaker, and when I click on the "Sound Preferences..."  there is an "Waiting for sound system to respond" message window appearing.

I do have a sound, but I can't do any sound preferences...  


Thanks for your help!

---

### Post by mikehartigan on 2011-09-13
Deleted the .pulse directory and the Sound Preferences opened up immediately - no restart necessary.  Cool! :)

---

### Post by treepete on 2011-09-23
i'm having the same problem "waiting for sound system to respond" and deleting the .pulse folder doesn't work. 
but i still have sound..

does anyone have a fix yet?

thanks

---

### Post by flexdream on 2011-10-09
deleting ~/.pulse and restarting worked for me. Thanks. :D

---

### Post by viraf87 on 2011-10-30
> **Ubuk2008 said:**
> Unfortunately, this method did not help me. What helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone

This worked for me and I'm using 11.04.  My ~/.pulse folder persisted on reappearing instantly too, however I found that quitting (that's Ctrl+Q not just close) any programs that use sound (I had Rhythmbox open) then deleting the folder stopped its reappearance.  

Hope that helps in case anyone's still having this problem...

---

### Post by morhin on 2011-11-30
Nothing was working so I decided to go back to the cd and see what it had in the software center that I might have changed. Figured it was a good place to start because it all worked there.

I installed all the PulseAudio stuff and then went to System>Preferences> (and that's when I saw) Pulse Audio Preferences.

I clicked on it and noticed that all of the boxes were unchecked soooooooo.........

In Network Access I checked Make discoverable PulseAudio network sound devices available locally.
In Network Server I checked Enable network access to local sound devices.
In Multicast/RTP I didn't check anything.
In Simultaneous Output I checked Add virtual output device for simultaneous output on all local sound cards.

I had no clue what I was doing as I'm a new newbie. But when I went back to System>Preferences>Sound, the Controller came back on screen and I was up and running.

I'm on an Acer Inspire 5250-BZ467

Still can't get the thing to shut of the external speakers when I plug in my headphones but I'll keep looking.

---

### Post by ttoolin on 2011-12-01
Thanks.  Deleting the .pulse directory, as described, worked well for me, but the loud sound darn near knocked my socks off when I rebooted :)

---

### Post by F W Adams on 2012-01-17
Removing ~./pulse didn't work for me. Selecting system/preferences/sound displays "Waiting for sound system to respond" after about 2 seconds. There is no sound icon in the top panel and trying to add it also leads to an error.

After removing ~./pulse it was created again but only with one file of zero bytes so I think it should have removed the problem.

Any one got any suggestions?

---

### Post by ChrisWebb on 2012-01-18
I got this after fiddling with HDMI audio support. The solution was to revert the changes I'd made, specifically in /etc/pulse/default.pa, and the restarting pulseaudio

```
sudo nano /etc/pulse/default.pa

```(remove changes, such as "load-module module-alsa-sink device=hw:1,7")

```

sudo service pulseaudio restart

```

---

### Post by F W Adams on 2012-01-18
Thanks for advice, in fact I wasn't aware of carrying out any changes so had nothing to undo. The first thing I knew was that it started behaving as described.

However I have know solved the problem and I think it might help others with broken sound systems. Someone suggested that with a broken sound system that one should try to set up another user, I did this and after the logon to the new user I got a message to say that ( a name I can't remember ) file was corrupted, delete or continue. It would not let me continue, only delete so I did. Amazingly when I then went back and logged on to the original user with the problem the same error message then occurred and I deleted the file as before. After this system/preferences/sound worked fine. All problems gone.

Even with the error present the sound was actually working but with no access to volume control unless it was allowed within the application program.

---

### Post by alierenerdal on 2012-12-09
thanks,its worked for me  .

---

