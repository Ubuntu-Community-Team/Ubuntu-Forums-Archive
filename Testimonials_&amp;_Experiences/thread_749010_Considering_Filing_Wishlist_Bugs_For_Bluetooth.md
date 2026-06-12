---
title: "Considering Filing Wishlist Bugs For Bluetooth"
date: 2008-04-08
forum: Testimonials &amp; Experiences
---

### Post by SneakyWho_am_i on 2008-04-08
I'm not sure if this is in the right place. I'm aware of wireless and networking support but I'm not looking for support per se. I am having an unfortunate experience with bluetooth and I was tempted to file a bug report but suspect that it might be more productive to go to the forum with it.

I have a Bluetooth Enabled Mobile Phone, and Xubuntu Hardy. Although my USB Bluetooth Dongle was plugged in when I installed, there was no interface thing for bluetooth communication - that's cool, I installed all the bluez, kdebluutooth and gnome-obex stuff.

All that made very little difference to the interface (not sure about stuff in the console, haven't bothered to look much) so I'm not sure where it all went.
[b]konqueror-kde4 still can't access bluetooth:/ urls.
Context Menu->Send To contains nothing new, and I can't add it manually because I can't find gnome-obex-sever
I can't use gnome-obex-send as it's not found, although I've installed its package I'm pretty sure.
The one thing that has changed is that there is now Applications->Accessories->Bluetooth File Sharing.[/b]

For the record, I did install Ubuntu's gnome desktop environment as well (the package and gnome itself) in an attempt to get Bluetooth sending.

Now this Bluetooth File sharing is all well and good, but its startup interface only has three functions:
1- the system tray icon thing displays an animation when the link is active
2- it has an "about" menu item
3- it lets you quit

So here comes my first thing. I have no way to send over bluetooth.
That's not a big problem for me, especially right now. If it really bothers me I will just download a tool from the internerd... It's probably all due to my particular setup. maybe I downloaded funky info from a repositroy. Maybe it's just not doable through Xubuntu. Maybe it's an issue in hardy; after all it's not suitable for use in production quite yet is it?

The really annoying meat of the thing though, is receiving files over bluetooth.
Every file I send to the PC ends up on my desktop. I'm sending a couple of thousand files, you know it's just not right and proper to have to pull them all off the desktop again.
For me it's easy - I can jsut type
```
mv ~/Desktop/*.3gp ~/3gp/
```
or something like that.

But that's not really very good, if I may say so. I'm certainly no computer programmer and don't understand the challenges involved. It's fantastic that we can do bluetooth stuff in Linux. It's stable, it's polished, it's far too simple to use.......
But if I were slightly more of a novice user than what I am now (first computer and OS?) then this would make me rather mad.I don't think that a total novice is going to want to have to sort and move a large number of OBEXed files off of their desktop. Some of them likely don't realise that their desktop is also accessible from a directory in the file manager (be it thunar or nautilus, dolphin or konqueror)

The other thing about it that's got under my skin to some extent is that after receiving an OBEXed file, it asks me what I want to do with the file:
- open
- delete
- close
Naturally I already know what all these files are, and I don't want to open them. So I pick close.

But remember I'm transferring quite a bit of stuff. If you transfer 1000 jpg files from your cell phone to your computer, that's a thousand little dialog boxes you have to close.
THE PROBLEM IS... I keep falling into this little trap, and clicking the big, attractive "close" button on the dialog.
You'll see 20 windows stacked in front of each other, so you start just clicking:
clickclickclickclickclickclickclick to close all the windows
The 21st window for some reason is pushed over to the right hand side slightly and you accidentally click "Delete"
So the file is gone from your computer and the dialog box closes.
GREAT.
So I lost a file, and I don't know which one it was. Thanks :D
Suddenly you have to check every file you were sending against every fiel you received and kept, to try to figure out which one you accidentally deleted.

So I'm looking for feedback on this suggestion I guess:
The as the Delete Button is so close to the big, attractive Close button, the "Delete" action should have a confirmation prompt.
If I wanted to delete it I would probably just use the desktop - after all, duh, the files go to my desktop every time anyway.

Deleting without prompting is especially bad due to the proximity of the buttons, and the sheer flood of damnable prompts that appear.


I know that there are workarounds.
I know I can press ALT+F4, ALT+Tab, ALT+F4, ALT+Tab
I know I can click, right click, close, click, right click, close, click, right click, close ( extra click because if you have too many similar windows open, it groups them on the taskbar but doesn't give them a communal close button)
I know that I can probably kill them with **killall** or something
And I know it might be just-ever-so-slightly-safer to close the windows using that tiny little camoflagued letter X in the top right hand corner of the screen....

But the Close button is RIGHT THERE in my face, and I fall for it almost every time! I admit, that makes me something of an idiot.

Nonetheless there are plenty of idiots out there like me, and if one of them deems it necessary to test his new computer by using bluetooth to transfer all the files of his phone, s/he's most likely in for a particularly nasty shock!

```
sneaky@ubuntu:~$ gnome-obex-send
bash: gnome-obex-send: command not found
```

I suppose that if you do know any really good *nix bluetooth push or bluetooth ftp-like programs, you could drop me a line. But I'm  more interested really in how the real problem might be approached - what to do for the people who can't fend for themselves at alll?

---

