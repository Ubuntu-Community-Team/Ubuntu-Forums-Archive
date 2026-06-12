---
title: "server locks on shutdown"
date: 2011-05-02
forum: Server Platforms
---

### Post by wlraider70 on 2011-05-02
When I shutdown my server it seems to lock up.
I use ssh for a headless unit and I can reboot fine, but I told it to shutdown and disconnected me and stopped logging (as far as i can tell) and then nothing.
The lights stayed on and I had to press the power button.

Is there a way to keep the logger running or to look someplace other then messages. I'm not great with logs.

---

### Post by arrrghhh on 2011-05-02
> **wlraider70 said:**
> When I shutdown my server it seems to lock up.
I use ssh for a headless unit and I can reboot fine, but I told it to shutdown and disconnected me and stopped logging (as far as i can tell) and then nothing.
The lights stayed on and I had to press the power button.

Is there a way to keep the logger running or to look someplace other then messages. I'm not great with logs.

Do you have a monitor hooked up to the server?

Might want to see what it's actually doing.  If the ssh service is stopped, then it'll obviously boot you out...

I'm also assuming you did ```
sudo shutdown -h now
``` Correct?  How long did you wait?  Perhaps it was syncing something...

---

### Post by wlraider70 on 2011-05-02
I don't have a monitor set up now, i was hoping the log would save me that trouble... I guess it wont.

Actually the command i sued was 

Sudo shutdown now

does the lack of a -h matter. I got logged out of ssh so i assumed it was working. Its possible I didn't wait long enough, but i had recently rebooted and i waited longer then that had taken to complete the entire reboot.

---

### Post by arrrghhh on 2011-05-02
> **wlraider70 said:**
> I don't have a monitor set up now, i was hoping the log would save me that trouble... I guess it wont.

Actually the command i sued was 

Sudo shutdown now

does the lack of a -h matter. I got logged out of ssh so i assumed it was working. Its possible I didn't wait long enough, but i had recently rebooted and i waited longer then that had taken to complete the entire reboot.

Well the monitor will let you see what's happening.  There might be something in /var/log, but off the top of my head I'm not sure what - probably something in messages, but the monitor will definitively tell you what's going on - at least in theory.

Now the command you submitted - try the -h, it means 'halt'.  I'm not sure what the command does without the -h, to be perfectly honest.

---

### Post by cipherboy_loc on 2011-05-02
The shutdown command (**sudo shutdown now**) without any flags is the same as saying **sudo init 3**, which isn't a full shutdown, but only a shutdown of most of the services. Thus you should add the -h flag (**sudo shutdown -h now**) to cause a complete shutdown (which equals **sudo init 0**)



Cipherboy

---

### Post by arrrghhh on 2011-05-02
> **cipherboy_loc said:**
> The shutdown command (**sudo shutdown now**) without any flags is the same as saying **sudo init 3**, which isn't a full shutdown, but only a shutdown of most of the services. Thus you should add the -h flag (**sudo shutdown -h now**) to cause a complete shutdown (which equals **sudo init 0**)

Ah, I knew there had to be a difference.  I wasn't savvy enough to realize what the difference was!

Thanks for laying this out, makes a lot of sense now!

---

### Post by volkswagner on 2011-05-02
```
sudo poweroff
```

Should be the same as

```
sudo shutdown now -h
```

So you may find it easier to type.

:)

---

### Post by cipherboy_loc on 2011-05-02
Or:

```

sudo halt

```

Eight letters + one space. ;) You could also add halt to the /etc/sudoers file such that you could run it just as:

```

halt

```

for only 4 characters. :D



Cipherboy

---

### Post by wlraider70 on 2011-05-03
thanks for the clarification -h took care of the problem.

---

