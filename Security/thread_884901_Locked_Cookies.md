---
title: "Locked Cookies??"
date: 2008-08-09
forum: Security
---

### Post by ub newb on 2008-08-09
3 days into the switch to ubuntu and I end up with an antivirus200(89)issue? Please help. 

I am running FF 3.0.1 and Ubuntu 8.04 OS only 


The FF browser is hijacked for only the user who was on the internet at the time that this "antivirus program" message first started running.An additional  FF window can be opened on this desktop and surfing is normal.

I cleared cache and cookies, and the problem remains that when opening FF from this users desktop, it goes straight to the antivirus page.  

When I look in the temp folder there are**[SIZE="4"] LOCKED COOKIES?????[/SIZE]** that I can not delete from the admin desktop or anywhere else, and even though I am not on the internet, other cookies keep popping into the temp folder. Some of them have the admin name attached to them. 

Whats up? 

FF works fine from other users desktops.

---

### Post by kerry_s on 2008-08-09
your not really making since.

by "temp" do you mean /tmp?
maybe put a screen shot, press print.
what add ons do you have in firefox?
have you tried putting renaming the settings folder? (open nautilus> press ctrl+h> rename .mozilla to mozilla.bak

---

### Post by ub newb on 2008-08-10
Sorry this didn't make sense. I was reading about the antivirus200(89)malicious program in the threads here to try to find out how to get FF back to normal.  

tmp is the folder I was referring to.(I'm still getting used to not having to view the world through Windows.) 

I ended up deleting the users desktop that was having the problem since this is a brand new install and there wasn't much on it yet. That seems to have solved the FF problem.

The locked icons on the stuff in the tmp folder is what freaked me out. I had two xp OS computers crash due to that antivirus thingy in the last three weeks so I am a bit jumpy.(:):):) Blessings in disguise as now I am a very happy ubuntu convert)

I went into the admin account and got rid of the stuff in the tmp folder, except for one locked icon file, they are all gone now. How do these locks work in the tmp file and should I leave stuff in there and not worry about it? Or should it be completely empty?

I still have one locked item in the tmp folder. Is this something to be concerned about? 

Thanks.

---

### Post by kerry_s on 2008-08-10
the /tmp file is exactly that, it's a temporary file were the programs you use can work out of, for instance vids will be saved there when played in the player, docs, pdf's, etc.... it is cleaned out at shutdown. i've never seen icons or cookies there, but then again i don't really look there that often. locks are used to protect the program if it's still in use, for example i've seen some plugins and add ons for firefox have lock files there. it's usually nothing to worry about. locks are a security measure.

mine looks like this:

---

