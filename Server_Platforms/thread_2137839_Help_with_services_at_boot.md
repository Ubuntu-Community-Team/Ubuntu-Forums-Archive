---
title: "Help with services at boot"
date: 2013-04-22
forum: Server Platforms
---

### Post by SlugSlug on 2013-04-22
I have a couple of services starting at boot (I used  sudo update-rc.d SERVICE defaults). 

These services can take about 5 - 10 seconds to load, druing this time my system waits for them.

Can I make it load more than 1 service at a time or is it best to start the service after X loads?

---

### Post by GameX2 on 2013-04-22
> **SlugSlug said:**
> I have a couple of services starting at boot (I used  sudo update-rc.d SERVICE defaults). 

These services can take about 5 - 10 seconds to load, druing this time my system waits for them.

Can I make it load more than 1 service at a time or is it best to start the service after X loads?

Same question here;
Using Boot-Up Manager ("Bum") isn't as much efficient as I thought.  They're probably a lot of services that can be still managed.

I've found out that delaying the startup applications after the login speed the process a lot.  Here's how you do it:

Let's say I want to slow down Guake Terminal of 10 second, I'll put this:
```
bash -c "sleep 10 && guake"
```

Simply enough.  Just make just in the Guake settings that "start at login" is unchecked.  Otherwise, it'll always had a "shutter" entry with no delay, to the Startup Applications.

All my applications are delayed a little now (Especially Dropbox.  Do this: bash -c "sleep 50 && dropbox start -i").  I guess I can get even more speed..

Thanks!

---

### Post by SlugSlug on 2013-04-22
Hiya thanks for your reply.

My setup is a little different, I believe in your case  the services are dependent upon you loggin into X where as I need mine to load without logging into but after X

---

### Post by GameX2 on 2013-04-22
> **SlugSlug said:**
> Hiya thanks for your reply.

My setup is a little different, I believe in your case  the services are dependent upon you loggin into X where as I need mine to load without logging into but after X

I understand;

There are programs that start after login (Those you can delay with my method), and the services that start after/before Plymouth splash.  I want to disable/delay some of these services, as well.

---

