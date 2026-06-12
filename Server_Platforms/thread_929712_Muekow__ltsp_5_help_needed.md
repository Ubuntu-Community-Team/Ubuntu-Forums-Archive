---
title: "Muekow / ltsp 5 help needed"
date: 2008-09-25
forum: Server Platforms
---

### Post by lykwydchykyn on 2008-09-25
(Sorry for the vague title, not sure how to phrase this succinctly.)

I have an LTSP 4.1 setup running on Dapper which I created a couple of years ago to power thin clients for our public library.  It's working like a champ, but of course Dapper goes out of support next year and I wanted to get up to speed with Muekow and LTSP 5.

So far I like what I see (yay NFS is gone!), but I have a couple of issues that I need to solve:

[COLOR="Silver"] - How do I prescribe (or at least suggest) a screen resolution for the clients?  I see where I can select color depth, but I saw nothing in the docs about resolution.[/COLOR] [COLOR="Red"]Never mind this one, I figured it out.[/COLOR]

 - If I'm at a client logged in through ldm and hit ctrl-alt-backspace, X dies as normal, but does not respawn (like it would normally).  How do I get it consistent?

By the way I'm using the default client build, I've only customized through the lts.conf file on the server.

Anyone got wisdom for me?

---

### Post by lykwydchykyn on 2008-09-25
Ok, never mind; I rebooted the server and now ldm is respawning.  Weird; I guess that's why I couldn't find anyone else with the problem.

---

### Post by lykwydchykyn on 2008-09-26
Ok, I speak to soon... which I guess is ok since I seem to be talking to myself ;-)

Anyway, I found the problem came back, and I'm starting to understand why.  My clients log in to a .xsession script to provide an endlessly respawning firefox.  The script looks something like this:

```

xfwm4 &
while true; do
    firefox
done

```

But somehow, even after a ctrl-alt-backspace, something is caching the session and the script is killing X11 whenever the user logs back in (I'm set up for autologin).  

So, where is the session being cached?  I've tried "killall -u kioskuser", but the session keeps coming back.  

Anyone have any ideas about this?  Or how I could ensure a persistent firefox instance without an infinite bash loop?

---

