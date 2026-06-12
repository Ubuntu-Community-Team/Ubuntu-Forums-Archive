---
title: "Firefox Erased All My Speed Dials..."
date: 2009-09-10
forum: The Cafe
---

### Post by sports fan Matt on 2009-09-10
Since Firefox had the Audacity to erase all my speed dials this morning after the update, I will no longer use it.  I attempted to retreive them reverting to an earlier version but to no avail.  Has anyone else lost all their settings and things like I did this morning?

---

### Post by Johnsie on 2009-09-10
Speed dials? 

Do you mean bookmarks? I use a plugin called FoxMarks that saves my  bookmarks on the Internet in case something goes wrong with my computer or I want to access them from another computer. That would probably help you make sure nothing like this happens again.

---

### Post by sports fan Matt on 2009-09-10
No..I use that one as well..I meant fast dials [https://addons.mozilla.org/en-US/firefox/addon/5721](https://addons.mozilla.org/en-US/firefox/addon/5721) Dials...

I saw the warning but and took the risk of installing it anyway (thinking it wouldn't be harmful, I was wrong) but Firefox anyway seems slow these days without many addons and Ive always seriously wanted to give Opera a good run..(like a new car)

---

### Post by Skripka on 2009-09-10
> **Johnsie said:**
> Speed dials? 

Do you mean bookmarks? I use a plugin called FoxMarks that saves my  bookmarks on the Internet in case something goes wrong with my computer or I want to access them from another computer. That would probably help you make sure nothing like this happens again.

I think he's griping about a 3rd party extension to FireFox, granting Opera's Speed Dial functionality, getting b0rked by an update.  Well.  That comes with the territory.  If you're afraid of loosing something, use something that provides similar functionality-but is backed up by being tested by the people who write the browser...I dunno like say, Opera in this instance.

---

### Post by Warpnow on 2009-09-10
Given chrome and the evolution of other webkit browsers, Firefox is soon to be a dying technology anyway.

---

### Post by qamelian on 2009-09-10
> **Warpnow said:**
> Given chrome and the evolution of other webkit browsers, Firefox is soon to be a dying technology anyway.
Not unless these other browsers come up with some compelling reason to switch. So far, no other browser out there is even close to meeting my needs.

---

### Post by FuturePilot on 2009-09-10
> **qamelian said:**
> Not unless these other browsers come up with some compelling reason to switch. So far, no other browser out there is even close to meeting my needs.

This ^

---

### Post by sports fan Matt on 2009-09-10
Skripka,

Yeah, I get what you mean.  FF just seems clunky.  No matter what I did to it to try to get things fast, they just weren't. I didn't like the fact I'd need to install x to get what I wanted.  Plus with Opera, I can use it's built in mail client saving room on my hard drive.  Now if only I can get dark text for every web page through my usercss styles...:)

Edit: May post a separate topic on where I need to point that file.

---

### Post by pwnst*r on 2009-09-10
not firefox's fault.

---

### Post by Tristam Green on 2009-09-10
Nope.  Third-party plugins don't necessarily have to maintain functionality across browser versions unless they themselves have been updated.

---

### Post by lovinglinux on 2009-09-10
Sorry to read about your problem. That's weird, because Speed Dial save dials as preferences entries, which are not erased even if you remove the extension. The Speed Dial thumbnails are stored under the **SDThumbs** folder in your profile directory.

Speed Dial also makes backups of the dials whenever you add new dials. They are stored under SDBackups.

What version of Firefox you were using and which version did you updated? Did you updated Speed Dial as well?  

I'm asking this because depending on the version of Firefox you were using before, your profile might be located elsewhere. For example, FF 3.5 currently uses ~/.mozilla/firefox-3.5 for storing profiles, while FF 3.0.x uses ~/.mozilla/firefox. So if you were using FF 3.5 and updated FF 3.0.x, it could be that FF 3.0.x replaced FF 3.5 launcher and now you are launching FF 3.0.x not knowing that your FF 3.5 profile is still intact at ~/.mozilla/firefox-3.5. Just guessing.

Anyway, if you want to still use Firefox I recommend my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). My Firefox runs almost as fast as Chromium and I have more than 40 extensions installed.

BTW, I also recommend daily backups of your FF profile. FEBE extension can do that automatically.

---

### Post by sports fan Matt on 2009-09-10
Was using FF 3.5 and tried to reinstall but have bigger issues..with the ubuntuzilla script as before..the icon is not the correct icon.  I deleted the mozilla profile and reinstalled 1st using the ubuntuzilla script and got a weird funky icon.  I really don't want to reinstall twice (i'm using karmic).  Is there any way I can get back the original FF Icon (reinstalling all my custimizations in FF isn't a big deal, have those saved)

Im not ready to give up on it completely, but I am frustrated..By the way I installed Thunderbird the same way and that didnt have an issue.

---

### Post by sports fan Matt on 2009-09-10
Here is the screenshot:

---

### Post by lovinglinux on 2009-09-10
> **sox fan Matt said:**
> Is there any way I can get back the original FF Icon (reinstalling all my custimizations in FF isn't a big deal, have those saved)

Go to "System >> Preferences >> Main Menu >> Internet. Right-click on the FF item in the and select "Properties", then click the default icon on the left, then change the address to /usr/share/pixmaps/firefox-3.0.png

---

### Post by sports fan Matt on 2009-09-10
I owe you a beer..that saved me hours of work..thank you

---

### Post by sports fan Matt on 2009-09-11
Ok, just getting back to the pc today and when I attempt to start FF I get "Failed to execute child process "Firefox" (No such file or directory"

---

### Post by seanmorry on 2010-12-29
This is how to fix the loss of the Speed Dials after you do 
the update.

You click on View, then on Toolbars, click on customized. 
After you click on customize a window will pop up with icons 
in it. Scroll down to the bottom and find the speed dial one 
and drag it into the toolbar. Then just click on the speed 
dial icon and all the dials will pop back up again. 

Sean

---

### Post by Quadunit404 on 2010-12-29
> **seanmorry said:**
> This is how to fix the loss of the Speed Dials after you do 
the update.

You click on View, then on Toolbars, click on customized. 
After you click on customize a window will pop up with icons 
in it. Scroll down to the bottom and find the speed dial one 
and drag it into the toolbar. Then just click on the speed 
dial icon and all the dials will pop back up again. 

Sean

And now the thread is revived, the mods frown...

---

### Post by Elfy on 2010-12-29
frown frown frown

---

