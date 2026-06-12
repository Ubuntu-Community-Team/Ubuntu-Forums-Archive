---
title: "Ubuntu Installation...."
date: 2007-02-06
forum: Utah Team - US
---

### Post by frozen007 on 2007-02-06
Hi Dear Members ,

i hav installed Ubuntu 6.1.10 onto my system successfully along side winXp.....

but problem is ...it is not detecting Keyboard when ever i boot with Ubuntu kernel....

so plz help me....

cheers 
frozen......

---

### Post by Rui Pais on 2007-02-06
hi,
probably you got a bad X config (/etc/X11/xorg.conf)

Since you installed that problem should not exist on your live CD. Try to boot from it a check what is it's xorg.conf (under Section "InputDevice") or at least post your actual xorg.conf here so any obvious error could be track.

good luck.

---

### Post by frozen007 on 2007-02-06
Thanx dear frd...


i willl let u know...sooon....

---

### Post by thenetduck on 2007-02-06
If you are having problems with the regular installation of Xorg I recommend reconfiguring it. I am guessing this will fix the bug. You can reconfigure it with this command. 

sudo dpkg-reconfigure xserver-xorg

There is a part that will configure your keyboard so I am guessing this will do the trick. 

 Hope this helps, 

 The Net Duck

---

### Post by frozen007 on 2007-02-07
Well FRND THANX FOR UR NICE SUGGETION.....

bUT,,,,,,, the problem is just like below.....

i hav made a live cd of Ubuntu.....and when i run the cd i got one desktop screen having two things on desktop....installl and examples icon.......and i found all things running well except keyboard....i opned text editor in accessories....but i was unable to type anything,,,,, only the mouse cursor came on editor but nothing was typing...........


But i continued to install the Ubuntu using Install icon on the desktop........

i got 6 steps to go for that.....
1..Language selection....
2. Zone selection ..
3.. and so on...

After that one window came asking for.....computer name.....user and password...etc...

Here came the big problem....i was unable to enter anything.....as keyboard was not detected....

and installation was stuck....
But i made a clever move.....and opened some .doc file that was there in the Live CD....and as mouse was working perfectly...i copied one word frm that file and pasted on all the fields..(user name ....password..etc...)....and i proceeded to next step of installation.....

i thought that things will allright after complete installation....

i booted the syatem and got ubuntu installed......i got one screen asking for USER NAME.....BUT AGAIN KEYBOARD WAS UNABLE TO FEED ANYTHING...SO NOW WOT I SHUD DO???????....


ONE MORE THING WHEN I RUN THE LIVE CD......I FOUND IN THE DEVICE MANAGER THAT NO KEYBOARD DEVICE DRIVER WAS THERE........


sO FRNDS PLZ HELP ME OUT......


cHeErS
froZEN....

---

### Post by Rui Pais on 2007-02-07
sorry, i don't quite understand your last post :(

If your keyboard works on liveCD why you just don't boot from there, 
mount you ubuntu partiticion, 
copy /etc/X11/xorg.conf to your mounted etc/X11 (you can backup your broken xorg.conf first),
reboot and after that (should be working by then) make any changes you want or need?

If you don't know how to do some of the above post that i (or others) can detail on that. 
There  is an app on liveCD, called Disks i think, that mount partitions with a GUI (a graphical interface)

good luck

---

### Post by frozen007 on 2007-02-07
well the problem is that my keyboard is not working,,, when i use Live cd also....
..

for few steps like ,,when booting frm cd starts.....keyboard is working but...when i get the desktop screen after booting is complete ,,the keyboard does not work at all.........


And in the applications.....>device manager..... >platform device...> the keyboard drivers r not there......


welll i willl see for ur last solution......


cheers
frozen...

---

### Post by thenetduck on 2007-02-08
Hi frozen, 
  Ok I think a good solution to your problem would be to start an onscreen keyboard. 

 This can be found at System --> Preferences -->Assistive Technology Preferences.

 You should then have the option to start an onscreen keyboard. After you start it, try reconfiguring X as recommended in my previous post. If the doesn't work give us another post. 

 The Net Duck

P.S. You might want to do this with the live CD if you can't log in.

---

### Post by xpod on 2007-02-08
If it`s a usb keyboard you may need to go in to your bios settings and "enable legacy\usb keyboard" or something like that,
I just had to do similar myself when swapping keyboards about:) .

---

### Post by frozen007 on 2007-02-12
Thanx DEar frnd....


i willl soon let u know..........if ur nice suggestion works...


Regards,

Frozen.....

---

### Post by frozen007 on 2007-02-15
Hi,


can u plz tell me some link where i can get keyboard drivers for Ubuntu Operating System......

as i think its problem wid drivers......

windows Xp my keyboard is working properly.....but when i shift to Ubuntu there r no drivers for keyborad even in Live CD....

Regards,
Frozen

---

### Post by thenetduck on 2007-02-16
Does it connect with a USB or no USB? Also you could please list the model number or name etc of the Keyboard? 

 Thanks, 
 The Net Duck

P.S. Did reconfiguring X with the on screen keyboard not work?

---

### Post by frozen007 on 2007-02-18
Well,

My keyboard is non USB keyboard....
Model Name: Standard 101/102 Keys or Microsoft Natural PS/2 Keyboard

Reconfiguring X.org with Onscreen Keyboard did not work....
when i run sudo dpkg-reconfigure xserver-xorg

one blue sceen came n it asked abt vedio drivers configurations........not for keyboard......

Regards ,
Frozen...

---

### Post by thenetduck on 2007-02-19
That's so odd that it doesn't ask you to configure your keyboard because when I do it, it does. Maybe it has something to do with if you select "Advance" or not? Hum don't know. 

   Ok I found this post on how to get things working correctly. I hope this helps you out. If this isn't the right key board, maybe there it will lead you in a better direction?  

 [http://www.ubuntuforums.org/showthread.php?t=229559&highlight=Microsoft+Natural+PS%2F2+Keyboard](http://www.ubuntuforums.org/showthread.php?t=229559&highlight=Microsoft+Natural+PS%2F2+Keyboard)

It look very good.

 The Net Duck

---

### Post by frozen007 on 2007-02-19
well thanx dear frnd...
i willl check it out if things work well...


Regards,
Frozen

---

### Post by frozen007 on 2007-03-12
Hi Dear Frnd...


well my problem not yet solved....


this time i m attaching  the xorg.config file.......


plz telll me wot changes i hav to make to solve the keyboard problem...

Regards
Frozen,,,

---

