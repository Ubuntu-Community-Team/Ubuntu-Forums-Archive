---
title: "suspend on lock screen"
date: 2012-04-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by bash321 on 2012-04-29
I have put my desktop computer into suspend mode using the sleep button that is on my logitech keyboard when i am logged in my system.

It then wakes up to the lock screen.

Is there away to put it back to sleep from the lock screen?
or using the sleep button on my keyboard again to make it go back to suspend mode from the lock screen?
so I do not have to login again and then press sleep?
could this be a feature for 12.10?
bash321
ubuntu 12.04 64 bit amd64

---

### Post by MacUntu on 2012-04-30
Hopefully not. If you are at the lock screen, the system doesn't know who you are (as you are locked out). I don't want a locked-out user to be able to change my system's state!

---

### Post by bash321 on 2012-04-30
I don't see how it is a security risk, as the only person that can make your computer sleep, is if it is a button that is pressed on a keyboard, which yes can be an unknown user, but it only goes to a suspend state, the machine does not go to a shutdown state. it would be the same as closing your lid on a laptop and the machine going into a suspend state to conserve power.
and plus the lockscreen prevents anybody from logging in! (except the user who knows the password)
I don't see why it could not be implemented.
as it is already implemented in windows.

---

### Post by arpanaut on 2012-04-30
> as it is already implemented in windows.

And when was that ever a good thing per se?

---

### Post by bash321 on 2012-04-30
It doesn't even have to be a button shown on the lockscreen.
It would be good if the suspend command could still work and apply when the lock screen is enabled so that if i press a button on my keyboard to initiate the suspend command, the computer can go back to sleep, without having to login and then press the suspend command.

or a setting can exist in system preferences in power management to turn this function on or off?

---

### Post by cariboo on 2012-04-30
I fail to understand why this would be a good idea, please explain. Just because Windows has it doesn't mean it's a good idea.

---

### Post by bash321 on 2012-04-30
I have a ubuntu AMD Quad Core desktop computer, that can go into a suspend state.
If I click the setting for shutdown and logout, I can also choose supsend or hibernate.
I can also use a sleep button on my logitech keyboard without using the mouse and clicking suspend through the menu's. which can also send the computer into a suspend state. I can then wake the computer using my keyboard which i think is enabled in my pc's bios settings which I have enabled. 
My Computer goes into a suspend state.
when it wakes up it goes to the lock screen to be able to login.
I do not want to be able to login! as sometimes I don't need to... it's easier. I have services which are run on a local network, not open to the internet, as a home media server, upnp service for ps3, or a smb server for local network file sharing or a local printer that is shared via CUPS.
These services start and run automatically when the computer wakes up sometimes even from the lock screen because...
there are also ways for these services not to start until they are run or started manually, but some of these services start from the suspend state because they have already been started before the computer went into a suspend state and resume once the computer wakes up.
Once i use these services and I am finished with using them. I then have to login go to the setting where the shutdown button is click suspend it requires a two step process. and put my pc back into a suspend state.
 Is there a way where I can just press the sleep button on my keyboard to make the computer go back into a suspend state from the lock screen?

Is there a service a Command line which I can enable or if some know's how to make a similar service so that I can send my computer to a suspend state using my keyboard from the lock screen instead of having to login......

---

### Post by cariboo on 2012-05-01
So are you saying that it comes out of suspend without your intervention? Or are you accidentally moving the mouse or hitting a key on the keyboard?

---

### Post by bash321 on 2012-05-01
i want the computer to wake up!
thats fine and normal... it can do that but it wakes up to the lock screen.. which is good for security. but sometimes i do not want to login (i just want to stay on the lock screen) to be able to use some of those background services i mentioned in my post above as i really do not need to login e.g. (just to print a page to a shared printer) , once i am finished with those services i should be able to just put my computer back into suspend mode using my keyboard like it can when i login, or using a one click method such as a button called suspend from the lock screen. instead of logging in and then putting into suspend mode.

but when i went to put it back into suspend i cannot do that from the lock screen!
i have to login to make computer go back into suspend mode. 
what im saying is that it does not go into suspend from the lock screen using the button on my keyboard.
but it does when i login!
i would like to be able to go into suspend from the lock screen, instead of having to login.

---

### Post by cariboo on 2012-05-01
Sorry about that, I glossed over the part where you said you were using your desktop as a server. I found a couple of questions/answers on askubuntu related to your last question about command line tools:

[http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line](http://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line)

[http://askubuntu.com/questions/78907/how-can-i-hibernate-suspend-from-the-command-line-and-do-so-at-a-specific-time-a](http://askubuntu.com/questions/78907/how-can-i-hibernate-suspend-from-the-command-line-and-do-so-at-a-specific-time-a)

---

### Post by bash321 on 2012-05-01
thanks for the quick reply,
ill make that more obvious and clear next time,i am running a small print server at home and sometimes smb server locally....

I remember I had problem with using suspend in ubuntu a while back... in a dev release of 11.10 when it was still in beta stage..
i had fixed it using those commands links above...
i'm not sure how it does it. but im guessing the logitech keyboard sets off that command to the computer when i am logged in when i press the suspend button for that action to happen. then the pc goes into suspend.
is there away for this command to be initiated when i am at the lock screen of my ubuntu pc? when i am not logged in and i press the button on my keyboard? because at the moment it does not work.

the command im guessing is sudo pmi action suspend...
but it only occurs when i am logged in not when i wake up at the lock screen.. it use to initiate suspend i think in ubuntu 9.04 or 9.10? it doesnt work in 12.04.

---

### Post by arpanaut on 2012-05-01
This is not a keyboard solution but can you not at the log-on screen click on the gear at the top right and select suspend?

Not exactly what you are looking for, but should work, also you could set a very short time to suspend in the Power section in System Settings.

---

### Post by bash321 on 2012-05-01
I can do that at the **logon **screen.
i can select i think shutdown restart not sure if there is suspend don't think so anyway. 
but I cannot do that at the lock screen when i resume from suspend.
is there away to do this at the lock screen?
even if meant putting that button from the logon screen to the lock screen as well?

---

### Post by bash321 on 2012-05-01
the power option is good as well in power management i will revisit that and have a brief look.
but it still would be good if i could manually put my pc to sleep using the sleep key on my logitech keyboard from the lockscreen, because then the computer would not randomly go to suspend when if i am reading an article for more than 5 minutes or watching a film using movie player. or going through automatic slideshow on LO or photo slideshow with shotwell and it randomly suspends because i haven't used the mouse and keyboard for more than 2 or 5 or 10 minutes.

---

### Post by arpanaut on 2012-05-01
My apologies, I don't suspend and don't lock screen, I mistook your saying unlock screen as logon screen.
Wasn't paying close enough attention, Sorry

---

