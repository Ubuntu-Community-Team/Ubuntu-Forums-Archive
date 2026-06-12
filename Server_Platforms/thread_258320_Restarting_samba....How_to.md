---
title: "Restarting samba....How to?"
date: 2006-09-15
forum: Server Platforms
---

### Post by 3r14nd on 2006-09-15
I'm trying to setup samba and I got it working to a point but....I had to go back and change some thing and now I can't firgure out how to restart it..

/ect/init.d/samba restart | stop | start

doesn't work it says that samba is not a file even though I can see   it in there.

if you edit that samba file it says to:

Start / Stop samba using nmbd and smbd

But when you run the nmbd it does nothing and when you run smbd it comes back and says aborted.

So Can i get some help here...Thank a million..

And If it matters I'm doing this through ssh.

---

### Post by NetworkGuy on 2006-09-15
>  
/ect/init.d/samba restart | stop | start 

Just in case you mistyped, Try 
```
/etc/init.d/samba restart 
```

---

### Post by 23meg on 2006-09-15
> /**ect**/init.d/samba restart | stop | startThat should be "etc" instead of "etc".

---

### Post by 3r14nd on 2006-09-15
it was a misspelling...sorry...

I was actually in the etc/init.d/ folder...

it's just a habit typing ect.. as in ectetera...or whatever it is..

but for some reason it worked this time....

I don't know...maybe i was misspelling it the whole time..

Thanx...I hate stupid mistakes..

---

