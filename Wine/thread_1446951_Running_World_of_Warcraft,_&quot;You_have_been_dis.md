---
title: "Running World of Warcraft, &quot;You have been disconnected from the server&quot; error"
date: 2010-04-04
forum: Wine
---

### Post by Spen on 2010-04-04
I can start up WoW just fine, but when I pick my character and try to log in I get the "You have been disconnected from the server" error.

Could anyone point me in the right way to get this fixed?

Thanks!

---

### Post by hikaricore on 2010-04-04
How long does the login attempt take?
If you're not zoning in quickly enough you will can be disconnected.

You might want to let us know a bit more about your system: video hardware/driver, amount of memory, etc.

---

### Post by Spen on 2010-04-04
When I log in and see my charter, and move around it will disconnect me.  Or as soon as I hit "Enter World" and the loading bar fills up all the way it will disconnect me.

My hardware is:
2gb of ram
8600gt
And a 1.8ghz core2duo

---

### Post by Zayfox on 2010-04-04
Delete Cache, WTF, and Interface folders.
Retry.

---

### Post by Spen on 2010-04-05
> **Zayfox said:**
> Delete Cache, WTF, and Interface folders.
Retry.


Gets me a little farther, it takes about 5 seconds( I can see people jumping around, ect) before I get disconnected.

---

### Post by hikaricore on 2010-04-05
> **Spen said:**
> Gets me a little farther, it takes about 5 seconds( I can see people jumping around, ect) before I get disconnected.

Are you sure your Nvidia driver is properly installed?
Are you running the game (as you should be) in OpenGL mode?
Have you disabled desktop effects?
Do other 3d games work?

---

### Post by Spen on 2010-04-05
> **hikaricore said:**
> Are you sure your Nvidia driver is properly installed?
Are you running the game (as you should be) in OpenGL mode?
Have you disabled desktop effects?
Do other 3d games work?


My drivers should be installed, I can use the cube/visual effects just fine.

I am running the game in OpenGL mode.

---

### Post by hikaricore on 2010-04-05
Should be and are don't exactly have the same meaning.
Check that you're using the latest proprietary nvidia driver and let us know what you find out.
I suspect you're using nv/nouevo or something instead.

---

### Post by Spen on 2010-04-05
> **hikaricore said:**
> Should be and are don't exactly have the same meaning.
Check that you're using the latest proprietary nvidia driver and let us know what you find out.
I suspect you're using nv/nouevo or something instead.

Thanks for helping so much,

should I get my drivers from here [http://www.nvidia.com/object/unix.html?](http://www.nvidia.com/object/unix.html?)

---

### Post by hikaricore on 2010-04-05
You should be able to install then from the repos, there are several guides around here but I would start by finding the restricted driver manager under your system menu.

---

### Post by Spen on 2010-04-05
In Hardware Drivers it says:

NVIDIA accelerated graphics driver (version current) [Recommended]


Then it has a green dot in the bottom left saying: "This driver is activated but not currently in use."

---

### Post by Spen on 2010-04-05
Just installed the drivers from nvidia's website.

Running: 195.36.15


Still the same problem.

---

### Post by hikaricore on 2010-04-05
You should have just enabled the driver in the restricted manager.
Now you're going to have a mess when you try and update packages.

I don't know what to tell ya, something's still not right.

---

