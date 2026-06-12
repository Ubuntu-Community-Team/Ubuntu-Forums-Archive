---
title: "backlight won't come on, on lemu1"
date: 2011-12-17
forum: System76 Support
---

### Post by dnarnold on 2011-12-17
Suddenly on my Lemur UltraThin lemu1, the backlight is not turning
on, so when I boot I get a black screen.  I can just barely
make out that the login box is displaying on the screen,
but it is essentially invisible without the backlight.
If I plug in an external screen or log on remotely,
the machine seems normal.

I am running Ubuntu 11.10 (oneiric ocelot) and have updated the
System76 drivers.
Using the function keys to change the brightness has no effect
on the laptop screen.

What can I do?  Thanks.

---

### Post by Lee_Machine on 2011-12-17
Assuming it's not a hardware issue try this

```
cat /proc/acpi/video/VGA/LCD/brightness
```

Where VGA, and LCD is the directroy for your monitor.

The vaules returned should look something like this:

```
levels:  12 25 37 50 62 75 87 100
current: 100
```

Then you just want to change the vaule to whatever you want, ie.

```
echo 75 > /proc/acpi/video/VGA/LCD/brightness
```

Did that work?

---

### Post by dnarnold on 2011-12-17
Thanks to Lee_Machine for the suggestion, but I don't have a
/proc/acpi/video directory.  Should I?

However I seemed to have solved the problem.  Although rebooting
did not help, I tried shutting down, removing the battery, and
rebooting on AC power only.  This time the backlight came on as normal
(a relief, I was afraid it was a hardware problem).  Then I popped
back in the battery, and now it seems normal (I can boot with
battery in).

I have no clue how it got messed up, but it seems to be fine now.

---

### Post by ubuntu27 on 2011-12-17
I have HP pavilion dv6000 laptops. Sometimes (not frequently) the screen is black when I turn on the computer.

I immediately turn off the computer, remove the battery and AC connection. After that I keep pressing the ON (power) button for 60 seconds.
Next, just plug in the battery and the AC back.
And voila! the laptop works.

I've learned this trick on many websites when searching for "black screen"

If 

Here are some samples:

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=55606](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=55606)

[http://getsatisfaction.com/hp/topics/hp_pavilion_dv6500_laptop_black_screen_6mths_old](http://getsatisfaction.com/hp/topics/hp_pavilion_dv6500_laptop_black_screen_6mths_old)

[http://getsatisfaction.com/hp/topics/hp_pavilion_dv6500_laptop_black_screen_6mths_old](http://getsatisfaction.com/hp/topics/hp_pavilion_dv6500_laptop_black_screen_6mths_old)


A video uploader asking for help on the same issue. See the the comment by "LassiPKTunn" on the video:

[https://www.youtube.com/watch?v=g3hF8k6W4YU](https://www.youtube.com/watch?v=g3hF8k6W4YU)

---

### Post by Lee_Machine on 2011-12-18
Sorry about that. I haven't been using Ubuntu for quite sometime and just recently starting using xubuntu as my main since I don't feel like rebuilding Arch right now :P

Anywho, it appears things are different in Ubuntu...no surprise there. I found how it's done now via command line, well one way.

```
sudo chown "username" /sys/class/backlight/acpi_video0/brightness 

``` 

```
sudo chmod 777 /sys/class/backlight/acpi_video0/brightness
```

This allows you to change the video settings. To make sure the numbers are the same as mind do this:

```
cat /sys/class/backlight/acpi_video0/brightness 

``` 

At max mine is set to 7 by default; which you can change that to. So to change the brightness up and down do:

```
sudo echo  7 > /sys/class/backlight/acpi_video0/brightness 

``` 

Where 7 is the highest you can go unless you change the max_brightness file.

Did this work for you?

---

### Post by isantop on 2011-12-19
> **dnarnold said:**
> Thanks to Lee_Machine for the suggestion, but I don't have a
/proc/acpi/video directory.  Should I?

However I seemed to have solved the problem.  Although rebooting
did not help, I tried shutting down, removing the battery, and
rebooting on AC power only.  This time the backlight came on as normal
(a relief, I was afraid it was a hardware problem).  Then I popped
back in the battery, and now it seems normal (I can boot with
battery in).

I have no clue how it got messed up, but it seems to be fine now.

I'd keep a close eye on this. The backlight shouldn't have any issues on a LemU1 on 11.10, so my guess is that this is some sort of hardware problem. If this happens again, and you can't get it to work, go ahead and send us an email and we will get it taken care of.

---

