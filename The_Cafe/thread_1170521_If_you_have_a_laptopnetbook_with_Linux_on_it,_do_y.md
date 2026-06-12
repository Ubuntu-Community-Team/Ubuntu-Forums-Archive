---
title: "If you have a laptop/netbook with Linux on it, do you suspend or shut down?"
date: 2009-05-26
forum: The Cafe
---

### Post by aysiu on 2009-05-26
I've been using Ubuntu for four years now, and I've seen the state of suspend-to-RAM get a lot better over the years.

Now I have an HP Mini, and I'm happy to say suspend-to-RAM works perfectly on the Mie it comes with (a customized Ubuntu 8.04 interface) and works almost perfectly (wireless is a little slow to connect afterwards) with standard Ubuntu 9.04.

So I pretty much suspend to RAM all the time. Occasionally, I'll shut down.

What do you all do?

---

### Post by gn2 on 2009-05-26
Usually suspend to RAM which works perfectly in 8.04 on my Asus F9E.

Shut down at night if I won't be using it the next day.

---

### Post by rax_m on 2009-05-26
Shutdown.. 

Sadly, upon resume from sleep sound doesn't work. And upon resume from hibernate my fans don't work properly!
My next laptop will definitely be more Linux compatible.

---

### Post by RaZe42 on 2009-05-26
I usually just shut down my laptop when I don't use it. Since it boots so fast it's no big deal.(I've also put GDM to autologin, so I can just leave the laptop to boot by itself while I do something else.)

Now if I only could speed up my BIOS :)

---

### Post by MaxIBoy on 2009-05-26
Usually, I suspend to RAM. Overnight, or when the battery is very low, I just shut it down, as cold boots are much faster than suspend-to-disk (especially after my boot time optimizations.)

---

### Post by FuturePilot on 2009-05-26
I usually hibernate my laptop at night, and suspend it during the day when I'm not using it. With this particular laptop I've never really had a problem with hibernate or suspend.

---

### Post by yoasif on 2009-05-26
i have to hibernate, because suspend does not work.

---

### Post by run1206 on 2009-05-26
i suspend to RAM

---

### Post by hessiess on 2009-05-26
Usuily suspend to ram, occationaly locks up while suspending requireing a force power off.

---

### Post by Simian Man on 2009-05-26
Suspend and hibernate both work flawlessly on my laptop, but take about the same amount of time as just shutting down and then starting up.  So I do that most of the time, but suspend when I want to keep my apps open.

---

### Post by gn2 on 2009-05-26
> **rax_m said:**
> Sadly, upon resume from sleep sound doesn't work.

You should be able to re-start it with a terminal command, e.g:

```
sudo /etc/init.d/alsa-utils restart

```
I have to do this on my desktop PC and created a panel launcher for it by right-clicking on the panel, then:

Add to panel > Custom Application Launcher > Type > Application in terminal
Name: Sound Restart
Command: sudo /etc/init.d/alsa-utils restart
Icon: /usr/share/icons/hicolor/scalable/apps/gnome-sound-properties.svg
Comment: Restart sound after suspend

---

### Post by Neheb on 2009-05-26
Because of dual-booting and having to use windows quite a lot (for ut3 editor, XNA and, before, c++) I usually shut down because I never know what OS I am going to have to start up when I use it next.

---

### Post by RiceMonster on 2009-05-26
hibernate if I'm taking it somewhere (its not plugged in) suspend if its on my desk or something. It suspends when I close the lid. I only reboot/shutdown for the ocassional kernal update or something.

---

### Post by wersdaluv on 2009-05-26
I'm fond of putting my computer to sleep. It uses very little battery in that state. Sleep is especially useful for me whenever I'm in school. To save battery life, I put my laptop to sleep whenever I move from a classroom to another or something like that.

---

### Post by Dragonbite on 2009-05-26
I shut down, my wife suspends to RAM.  With the faster jaunty boot-up I'm not loosing all that much time starting from OFF or SUSPEND so might as well make it a cleaner bootup.

Now, part of that could be because I only have 512 MB of RAM.  Perhaps if I increase that then Suspend will be faster and I may change my mind.

---

### Post by RiceMonster on 2009-05-26
Suspend is lighning fast for me; it's pretty much instantanious. I have 2GB of ram. Hibernate is a little slow, however.

---

### Post by SuperSonic4 on 2009-05-26
I shutdown the laptop if I'm not using for more than half an hour

---

### Post by Idaho Dan on 2009-05-26
I always shut down. 
I never have tried suspend. HP Pavilion ZV6130US.

---

### Post by aeiah on 2009-05-26
usually shutdown. we have an acer aspire one. i say we because me and my girlfriend bought it together. she takes it on her commute during the week and i think she just closes the lid (suspend to ram).

i havent done tests to see how much battery it uses in this state but its probably so little that i might as well use it. hibernate to disk takes about 15 sec to boot up and boot from power off takes about 20 seconds so there isnt much point using that, plus it also means that a thief has automatically bypassed the BIOS password.

---

### Post by ghindo on 2009-05-26
It's a tossup between shutting down and suspending to RAM.  If I'm going to move my laptop around, I'll shut it down.  If I'm going to leave it in one place, I'll use suspend (which works flawlessly for me).

---

### Post by pookiebear on 2009-05-26
shutdown cause I am using it all day and I shut it down at night when I am sleeping.

---

### Post by Warpnow on 2009-05-26
Shutdown.

My Kuki Linux on the AA1 boots in under 10 seconds, so...why not?

---

### Post by dragos240 on 2009-05-26
When I suspend any computer something wrong happens every time.... I ALWAYS shut down.

---

### Post by billgoldberg on 2009-05-26
> **aysiu said:**
> I've been using Ubuntu for four years now, and I've seen the state of suspend-to-RAM get a lot better over the years.

Now I have an HP Mini, and I'm happy to say suspend-to-RAM works perfectly on the Mie it comes with (a customized Ubuntu 8.04 interface) and works almost perfectly (wireless is a little slow to connect afterwards) with standard Ubuntu 9.04.

So I pretty much suspend to RAM all the time. Occasionally, I'll shut down.

What do you all do?

Suspend and hibernation work, but with Jaunty's bootup speeds I don't need them.

---

### Post by raymondh on 2009-05-26
suspend during the day ... shutdown at night

---

### Post by lethalfang on 2009-05-26
My laptop cannot wake up from suspend or hibernate. 
When it tries to wake up, I'm usually stuck at the password prompt but I cannot type on it. The mouse moves around okay, but I'm not sure the click is working because I can't get the cursor in the typing-box to start blinking, and the keyboard is unresponsive.

---

### Post by LowSky on 2009-05-26
I have a Lenovo S10, I usually just shut down, but I have used the other methods every once in a while and they all work flawlessly, at least they seem to... hmm now you have me guessing... when I get home I'm checking...lol

---

### Post by don_quixote on 2009-05-26
Hibernate.  Suspend to RAM is the one thing that does NOT work on my lappy.

---

### Post by don_quixote on 2009-05-26
> **lethalfang said:**
> My laptop cannot wake up from suspend or hibernate. 
When it tries to wake up, I'm usually stuck at the password prompt but I cannot type on it. The mouse moves around okay, but I'm not sure the click is working because I can't get the cursor in the typing-box to start blinking, and the keyboard is unresponsive.

Have you tried these instructions?

[http://ubuntuforums.org/showthread.php?t=752647&highlight=ubuntu+suspend](http://ubuntuforums.org/showthread.php?t=752647&highlight=ubuntu+suspend)

---

### Post by Einsamkeit on 2009-05-26
Hibernate/Sleep works flawlessly, but when I don't use my equipment I try to shut it down, minimizing power usage / hardware wear&tear.

---

### Post by Xbehave on 2009-05-26
shutdown when im done, hibernate when im not

my suspend doesn't work (acer aspire 5101), i know what i need to do to fix it but i the system doesn't seam to responds to the correct settings (i have a manual script that i can run but doesn't always work). Also my computer crashes so often (hardware fault) that I save everything to disk ASAP so no need to suspend!

---

### Post by Trail on 2009-05-27
I don't get the deal with hibernate and suspend. It would save me, what, 20 seconds? I don't bother. I always shut down.

---

### Post by Erik Trybom on 2009-05-27
> **Trail said:**
> I don't get the deal with hibernate and suspend. It would save me, what, 20 seconds? I don't bother. I always shut down.
It's not just that it starts quicker, it's that you can continue working right where you left off. All programs and open documents remain exactly where you left them. This can save anything from a few seconds to several minutes depending on what you're doing and how many applications you have open.

---

### Post by kerry_s on 2009-05-27
i always suspend if i can, i'm on & off the computer constantly, could be every couple of minutes, could be hours, it just doesn't make sense to keep turning it on & off.
it took me forever to get suspend right on this junker of a desktop though.
i finally figured out i had to add "acpi_sleep=s3_bios" to grub and i had to add "ADD_PARAMETERS="--quirk-s3-bios" " to /etc/pm/config.d/config
no more black screens or dead monitor on resume now, it just works perfectly everytime.

---

### Post by lisati on 2009-05-27
I *have* to shut down on the laptop I normally use for Ubuntu - the battery charging department seems to have gone south some time ago (haven't had the patience, inclination or budget to do major troubleshooting, repairs or replacement) and I like to turn the home computer department off at the wall each night.

---

### Post by Kingsley on 2009-05-27
The blue power light on my laptop blinks when the computer is suspended. That bothers the hell out of me at night when I'm trying to sleep, so I have to shut down.

---

### Post by gn2 on 2009-05-27
You could disconnect the light?

Edit: oops, forgot it was a laptop :redface:

---

### Post by spupy on 2009-05-27
I think Suspend it awesome. While waiting for my friends' laptops to load, I just flip the lid and TA-DAAA. Only the mac guy can rival the speed. Going to sleep - why bother saving files, closing programs, clicking shutdown - just close the lid. Need to check your mail/calendar - why wait 1 minute - just open the lid.

---

### Post by Stefanie on 2009-05-27
I usually hibernate my laptop (and even my desktop because I want to keep my apps open). My eee is running pure openbox so the gnome/kde suspend/hibernate aren't avalailable, but I just discovered that sudo pm-suspend works really well so I'll probably start using that now :-)

---

### Post by Dragonbite on 2009-05-27
> **Kingsley said:**
> The blue power light on my laptop blinks when the computer is suspended. That bothers the hell out of me at night when I'm trying to sleep, so I have to shut down.

Black electrical tape?  May not look good during the day but should do the trick at night! 

I'm glad for the slowly-fading light because I have 2 hard drives for my laptop and this light tells me if my wife has suspended her system or not. If she has, I have to go in and shut it down first, otherwise it's free game to pull out the old hard drive and put in the new.

---

### Post by mamamia88 on 2009-05-27
always suspend.  i'm on a mission to see if i can keep this laptop on for 6 months until next release

---

### Post by automaton26 on 2009-05-27
I never know whether I'm going to restart in Windows or Linux next time, so I have to shutdown.

I also unplug my laptop - I'm not paying to heat the room by leaving the power adapter ever-so-slightly warm ;)

---

### Post by emeraldgirl08 on 2009-05-27
I've never put my computers in suspend. It's a concern of electrical-usage and habit that I shut it down.

I've read here on the forums of members who had their laptops turn into a zombie because of suspending.

---

### Post by init1 on 2009-05-27
I would probably use suspend more if it worked in Ubuntu.

---

### Post by JohnFH on 2009-05-27
> **init1 said:**
> I would probably use suspend more if it worked in Ubuntu.

It does.

---

### Post by Xbehave on 2009-05-27
> **automaton26 said:**
> I never know whether I'm going to restart in Windows or Linux next time, so I have to shutdown.
Hibernate will still go through grub on bootup so you can hibernate (but not suspend) and then boot into windows anyway. If you wanted you could hibernate both windows and Linux separately and still boot into either.

Updated my vbe file and now my resume script workds again :D (debian), but i only suspend if i know im going to be using the box v.soon (e.g if im carrying the laptop to another room as otherwise it will crash)

my script fixes the screen when its gone crazy
i made a vbe file ```
sudo "vbetool vbestate save > vbe"
```
then when it goes crazy on resume run:
```
kdesu -c "vbetool vbestate restore < vbe" 
```
anybody know what i have to edit to get it working by default

---

### Post by init1 on 2009-05-27
> **JohnFH said:**
> It does.
Not on my laptop.

---

### Post by aysiu on 2009-05-27
> **JohnFH said:**
> It does.
It depends on your hardware configuration.

---

### Post by Vostrocity on 2009-05-27
Hibernate is definitely the future. Notice how Vista puts Hibernate as the default over Shut Down? Back when I only used Vista, the only times I had to completely shut down my computer was when it crashed. Unfortunately Hibernate in Ubuntu isn't working for me so I use Suspend.


And can someone explain to me what that patchwork cat thing is that everyone uses for their avatar?

---

### Post by aysiu on 2009-05-27
> **Vostrocity said:**
> Hibernate is definitely the future. I hope it's not the near future, because I have 2 GB of RAM and a 16 GB SSD. Do you know how big my swap partition would have to be for hibernate to work properly (right now my swap partition is non-existent)?

---

### Post by Dragonbite on 2009-05-27
> **aysiu said:**
> I hope it's not the near future, because I have 2 GB of RAM and a 16 GB SSD. Do you know how big my swap partition would have to be for hibernate to work properly (right now my swap partition is non-existent)?

That's the only reason for me keeping a swap partition. Otherwise, I rarely use it anyhow and that's with a measly 512 MB of Ram!

---

### Post by Xbehave on 2009-05-27
> **aysiu said:**
> I hope it's not the near future, because I have 2 GB of RAM and a 16 GB SSD. Do you know how big my swap partition would have to be for hibernate to work properly (right now my swap partition is non-existent)?
using swap for hibernate is an "it works" hack for linux, i hope eventually (probably once hibernation is well designed in the kernel) that hibernation tools will be better designed in userspace too. If you have no swap but your disk isn't full you may want to use a hibernate file(a swap file just for hibernating)
it is also unlikely that you need 2GB to hibernate i need ~80% of **used**(not just cached) memory to suspend, so if your good with bash scripts you could create a hibernate file on demand and have it created at the correct size, otherwise trial and error (or watching your system suspend by disabling usplash) will probably tell you how big the file has to be.

>              total       used       free     shared    buffers     cached
Mem:          1473       1461         12          0         49        769
Swap:          951        134        817

I hibernate fine with 951M swap but 1473M ram (and i use that ram for stuff like /tmp too)

---

