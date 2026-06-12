---
title: "Why does the Logout Screen freeze already running programs?"
date: 2008-04-17
forum: Security Discussions
---

### Post by sweatingegg on 2008-04-17
Choosing System > Quit stops already running processes. I am wondering why the Logout Screen freeze already running processes?

I guess it may be from a security issue.

If there is no reason, please change it not to freeze already running processes.

Thanks in advance.

---

### Post by The Cog on 2008-04-17
It's the standard unix behaviour. Whenever a user logs out, all the programs running on his terminal are killed. You can take measures to protect concole applications, but in general you're not going to be able to leave GUI apps running.

---

### Post by cdenley on 2008-04-17
> I am wondering why the Logout Screen freeze already running processes?
When you bring up the logout menu, it freezes the screen so it can fade. The processes are still running, you just can't see them because you're looking at a faded screen capture.

---

### Post by sweatingegg on 2008-04-18
I think you guys dont understand what I mean.

I mean that when Logout screen appears, already running processes suspend their operation. And I am wondering why the Logout screen prevents already running processes from continuing their operation. I dont mean executing Logout but just showing the Logout screen.

---

### Post by sweatingegg on 2008-04-18
> **cdenley said:**
> The processes are still running, you just can't see them because you're looking at a faded screen capture.

Yes, the processes are alive but suspend their operation.

---

### Post by The Cog on 2008-04-18
Ah. I see what you mean. cdenley is right - the screen is frozen but the app continues. Try opening a terminal and use the command **ping localhost**. This counts up at one second intervals. When the screen is dimmed, the command is stilll running in the background and the screen catches up when you hit cancel. 

I suspect the dimming is not the real screen. I think gdm takes a snapshot of the real screen and then goes full screen with it to hide the real screen. I suspect that screensavers do much the same thing. But this is only speculation.

---

### Post by sweatingegg on 2008-04-18
please check whether a process is suspended or keep running:


test.c
==============
#include <stdio.h>

main()
{
   int i;

   while (1)
   {
      printf("cnt: %d\n", i++);
   }
}
==============
you can build it by typing in terminal:
gcc -o test test.c

And you run the test program by typing in terminal:
./test

You can check that the Logout screen suspend the test process!

---

### Post by /etc/init.d/ on 2008-04-18
Have a video playing in the background.  With VLC at least, the sound will stop a few seconds after the logout screen appears and the screen fades.

---

### Post by cdenley on 2008-04-18
I see what you mean when running your code in gnome-terminal. However, even though you can't see it when you click cancel on the logout window, it is still counting. When I wait a few seconds, it continues at the count you would expect it to have. I'm guessing this initial lag has something to do with graphics events being queued while the screen is frozen. Using xterm does not show this lag. If you add a sleep to your infinite loop, you won't see this lag either. Your program doesn't suspend, freeze, or terminate.

```

#include <stdio.h>
main()
{
        int i;
        while (1)
        {
                sleep(1);
                printf("cnt: %d\n", i++);
        }
}

```

---

### Post by cdenley on 2008-04-18
> **/etc/init.d/ said:**
> Have a video playing in the background.  With VLC at least, the sound will stop a few seconds after the logout screen appears and the screen fades.

I tried mplayer. The audio continues. The video is replaced with a blue box because screen captures don't capture overlay video.

---

### Post by sweatingegg on 2008-04-18
> **cdenley said:**
> However, even though you can't see it when you click cancel on the logout window, it is still counting. 

Really?

Above test code is just a siimple example. And my multi-thread program does not run during Logout screen in Ubuntu. I tested it in x86 and x86_64 machines.

I am an application developer and just want to test it in Ubuntu.

Please run the above code in Fedora and then run "Quit".

The logout screen of Ubuntu has a problem that suspends already running processes.

> **cdenley said:**
> If you add a sleep to your infinite loop, you won't see this lag either. Your program doesn't suspend, freeze, or terminate.

And you did not mention why I should add a sleep().

---

### Post by cdenley on 2008-04-18
> 
And you did not mention why I should add a sleep().


I'm not sure why the output in gnome-terminal lags after the logout menu is canceled. As I said, my guess is that it has to do with queuing graphics events. Every time the program prints a line of output, gnome-terminal has to print that output. Maybe, when the logout menu is opened, gnome or gnome-terminal knows it can't redraw the output while the screen is frozen, so it queues it so it can be updated later. Then maybe when you cancel the logout, it has to go through the entire queue before the terminal is redrawn. I'm not a gnome developer, and this is just an educated guess. I was just making an observation that might help point you in the right direction. Does your application you're having problems with use graphics? What makes you think it gets suspended?

I tried running this script before logging out to check the status of another process. When I clicked cancel, I saw a bunch of R's, which indicate the process was running, not suspended. A suspended process would give a status code T.
```

#!/bin/sh
while [ 1 ]
do
        ps -p 26339 -o pid,state=
        sleep 2;
done

```

---

### Post by sweatingegg on 2008-04-18
I can check it using xterm too. And my multi-thread program starts in /gdm/PostLogin/Default script.

Running my test code in Fedora would help clearing this problem.

Thanks.

(please change "int i;" to "int i=0;" :))

---

### Post by sweatingegg on 2008-04-18
FYI, here is my program demo videos: [http://www.clixon.co.kr/english/bbs/index.php?mode=view&code=evod&uid=9](http://www.clixon.co.kr/english/bbs/index.php?mode=view&code=evod&uid=9)

Assuming Ubuntu machine be a Sub computer that does not have a keyboard/mouse, Logout screen suspends my program and in that case, user cannot share keyboard/mouse data with the Ubuntu machine displaying Logout screen.

If my customer will ask why this probem occurs, I cannot help telling them, "Please use other Linux except Ubuntu."

---

### Post by cdenley on 2008-04-18
Are you using gnome in fedora? Does it have the fade effect on the logout menu? Do you have the same problem with other commands that use the fade?
```

gksu /usr/sbin/synaptic

```
I'm not sure how to disable the fade for the logout menu. You can disable the logout menu entirely with
```

gconftool -t bool -s /apps/gnome-session/options/logout_prompt false

```

You can look at the source for the logout
```

apt-get source gnome-session

```

---

### Post by sweatingegg on 2008-04-19
I tested it on both GNOME and KDE of Fedora7 & 8. GNOME logout screen does not have the fade effect, but though KDE logout screen has the fade effect (the fade effect of the KDE logout screen in Fedora is very similar with the one of Ubuntu), the KDE logout screen does not suspend already running processes at all.

Please look at the first demo video in previously mentioned site and you can watch the fade effect of KDE in Fedora 7 in first 1 minute part of the video.

I remember that the earlier version of KDE (in Fedora Core 4) had the same problem, but recent KDE version (in Fedora 7 or 8 ) fixed the problem.

Sorry. Fixing this issue is not my job. Please regard my posting as a bug report.

---

### Post by cdenley on 2008-04-19
I doubt anyone whose job is to fix it would happen to read this. You might want to file a real bug report if you want it to work differently on future releases. You will need to provide steps to reproduce the bug, which would probably require sample code. I don't think the infinite loop code you posted demonstrates a bug in gnome-session. I posted the command to retrieve the code so you might be able to figure out why your program isn't working, and find a workaround.

[https://bugs.launchpad.net/ubuntu/+source/gnome-session](https://bugs.launchpad.net/ubuntu/+source/gnome-session)

---

