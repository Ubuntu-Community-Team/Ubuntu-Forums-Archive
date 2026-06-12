---
title: "A security issue with Ubuntu Server"
date: 2010-11-10
forum: Security
---

### Post by TheAlien on 2010-11-10
If one has system encryption on an Ubuntu Server machine, and you log out, and another person has physical access to the computer, he can press alt+left to see how many characters the system encryption password has. Since that first screen contains some boot info and is not cleared.

Is there a way to clear that screen or not make it appear at all during and after boot?

---

### Post by CharlesA on 2010-11-10
The console screen?

Care to explain with screen shots or something?

---

### Post by cariboo on 2010-11-10
I assume the op is using a gui on his server, as I've never seen any characters echoed back from a command line.

---

### Post by CharlesA on 2010-11-10
> **cariboo907 said:**
> I assume the op is using a gui on his server, as I've never seen any characters echoed back from a command line.

That echos my observations as well. I know that it echos stuff like system messages to tty1 like when you plug in a thumb drive, but I don't recall of it echoing anything other then that.

We'd really need more info.

---

### Post by TheAlien on 2010-11-11
I'm not using a GUI, I'm using the default Ubuntu Server system.

When you start up the computer, and you're prompted with the system encryption password, the characters are echoed back as stars '[COLOR=Red]*[/COLOR]'. When the password is entered and you continue, some more information about the system startup is shown on your screen, like mounting, starting AppArmor and Apache, among other stuff.

Then the screen gets blank and you're prompted with the login on the top left corner.

This is just the default Ubuntu Server startup procedure that most of us already know about.

But if you now push ALT+LEFT, you'll be switching back to the previous screen that was printing the startup procedure. This screen shows the system encryption password entered as stars, in other words it shows how many characters that password contains.

IMO this is a big deal, because an enemy can just push ALT+LEFT until he/she gets to that startup screen, and then know how many characters that important password contains, making brute force attacks way more convenient. On another hand, it's not a very big deal for me if I have the possibility to clear this screen somehow either before or after I login. i guess that's my question here.

This screen is a screen in addition to all the tty login screens that can be accessed at anytime by using ALT+LEFT/RIGHT, even though all consoles are logged out, unless you install a console locker application. But I'd rather be able to wipe that screen blank instead of installing an application from Universe and have to be logged in always just to do that.

I hope I made this more clear now. :)

---

### Post by CharlesA on 2010-11-11
Interesting.. I didn't know about that hot key combo (It looks like it switches to a different TTY).

What encryption software are you using and what did you tell it to encrypt?

EDIT: It looks like the one you are looking at is TTY7, since that displays the bootup messages and stuff.

---

### Post by cariboo on 2010-11-11
My server is headless, so I have to access it via ssh, when I press Alt-Left or Alt-Right all I get is C for Alt-left and D for Alt-right.

My server is a week old 10.04 install, it is a personal file server with nothing open to the outside world.

---

### Post by CharlesA on 2010-11-11
> **cariboo907 said:**
> My server is headless, so I have to access it via ssh, when I press Alt-Left or Alt-Right all I get is C for Alt-left and D for Alt-right.

My server is a week old 10.04 install, it is a personal file server with nothing open to the outside world.

Yep. It only works if you are looking at the physical console (or in my case a "physical console" on a VM).

It looks like that hotkey switches between TTY terminals, the same as Ctrl + Alt + (F1 thru F7)

---

### Post by TheAlien on 2010-11-13
> **CharlesA said:**
> Interesting.. I didn't know about that hot key combo (It looks like it switches to a different TTY).

What encryption software are you using and what did you tell it to encrypt?

EDIT: It looks like the one you are looking at is TTY7, since that displays the bootup messages and stuff.

I'm using the alternate install CD and sets up a physical volume for encryption with dm-crypt. I'm encrypting everything except /boot, so you could call it a full system encryption if you like.

Do you think it's possible to clear that screen as root/sudo after having logged in?

---

### Post by CharlesA on 2010-11-13
I don't know. Maybe submit a bug report on launchpad about it?

Google didn't produce anything worthwhile.

I think it would be ok if the encryption key wasn't echoed to the screen.

---

### Post by cariboo on 2010-11-13
This [wiki page ]("https://wiki.ubuntu.com/ScreenProfiles") seems to point to where the problem is, I would definitely file a bug, as this type of behavior is not needed or wanted.

---

