---
title: "multiple screen calls in my local.etc for startup"
date: 2007-12-25
forum: Server Platforms
---

### Post by fizgig on 2007-12-25
I'm trying to run two different screen sessions automatically on my server when it boots.  Here's what my rc.local looks like now:

> su matt -c "screen -d -m /home/matt/somescript1"
su matt -c "screen -d -m /home/matt/somescript2"
When I run "screen" I'm told that I have two unattached screens that don't have anything to do with each other so which one do I want to connect to...

I wanted both screen commands to be associated so I can cycle through them.  Anyone know how?

---

### Post by koenn on 2007-12-27
what is it that you're trying to achieve ? why do you want startup scripts run by screen ? 
what do you mean 'cycle through them ' ? 

I've had a quick look at screen, seems to me you can easily run 2  or more screens, than reattach to them at will with screen -r  or screen -x 

eg
```

@knix:~$ screen -d -m ping www.google.com
@knix:~$ screen -d -m ping www.ubuntuforums.org
@knix:~$ screen -r
There are several suitable screens on:
        6397..knix      (Detached)
        6423..knix      (Detached)
        6294.pts-3.knix (Attached)
        6227.pts-4.knix (Attached)


@knix:~$ screen -r 6423..knix 

64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=230 ttl=51 time=20.4 ms


```

---

### Post by fizgig on 2007-12-27
I'm trying to run some programs that I can have access to later when I ssh in.  Screen is the only solution I'm aware of and it works for the first line but not for additional lines.

You are correct, you can reattach by specifying which screen you want to connect to.

When you run screen manually and start a program like the ping example, you can then hit Ctrl-A and then "c" to start a new session with a new prompt and then run another program in that prompt.  After that you can cycle between them by hitting Ctrl-A and then "n" to get to the next session.  You can have as many sessions as you'd like.

That's what I'd like to have done here - have all programs attached to the same screen.

---

### Post by koenn on 2007-12-28
I can't get my head around screen yet - it would seem that for what you want, you need to start each screen session from within the previous session. I don't know if I understand it correctly, and I don't see how you'd script that.

---

