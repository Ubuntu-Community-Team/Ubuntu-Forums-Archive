---
title: "Hotmail and Firefox"
date: 2008-08-08
forum: Testimonials &amp; Experiences
---

### Post by Slug71 on 2008-08-08
Anybody else having issues when you log into Hotmail and it asks you to upgrade your version of Firefox even though you have the latest installed?

---

### Post by timcredible on 2008-08-08
my sister-in-law has hotmail and ie is broken on her windows machine (probably has something to do with the fact that verizon, google, hotmail, aol, and yahoo have all added stuff to ie on her machine), so she uses firefox, and hotmail works ok on it.  she doesn't want to upgrade to the newer hotmail though, so i don't know if there's some issue with it.  but, since hotmail is a microsoft service, i wouldn't be surprised if they made the new version to specifically not work correctly with anything but ie.  as a linux user, you may want to move your email off a linux-unfriendly mail service.

---

### Post by ubuntu27 on 2008-08-08
I had the same trouble one or twice.

The trouble that I had with Hotmail&Firefox is that when I try to log-in to Hotmail, it will ALWAYS tell me that I have inputted the wrong password. 
I have to try to login the second time to work.


It is really annoying! The first time always fails.

---

### Post by Slug71 on 2008-08-08
Your sister-in-law should be able to remove all those add-ons in add/remove programs. They should all be toolbars.

I also thought it might be a compatibility issue but it says in that screen you should use the latest versions of IE, Firefox and another one. and then if you click Firefox it wants you to install firefox 3 which im already using with Ubuntu. I dunno weird but it must support Firefox if it has that option. It only allows me to use the Classic version of the new Hotmail and not the Full one.

---

### Post by ooobuntooo on 2008-08-08
Hotmail works fine for me in Linux. I have heard about other people having problems with it. Why not use gmail?

---

### Post by Slug71 on 2008-08-08
I could but ive had my email address for so long etc.
But then the further you get away from anything Microsoft the better.

---

### Post by karellen on 2008-08-08
you're right, hotmail tells the same to me, though it lets you log in in a stripped down version

---

### Post by Slug71 on 2008-08-08
yeah exactly.

---

### Post by AmericanYellow on 2008-08-08
> **Slug71 said:**
> Anybody else having issues when you log into Hotmail and it asks you to upgrade your version of Firefox even though you have the latest installed?

Somewhere on the page is a link that you can click that will take you to classic Hotmail and that works properly.

The reason  you are having troubles is that Microsft has finally decided to allow the full version of the new Hotmail to work on Firefox and are not fixing the bugs or something. For me, the full version has already started working completely. :)

---

### Post by bartos on 2008-08-08
I had the same problem with Sabayon. I found Firefox was labeled Gentoo. Check Help tab and what About says.

Any changes you need to make can be done by typing about:config in the address bar.Just change "general.useragent.vendor" to a blank line if there is anything in it.

---

### Post by robelliott2125 on 2008-08-21
> **bartos said:**
> I had the same problem with Sabayon. I found Firefox was labeled Gentoo. Check Help tab and what About says.

Any changes you need to make can be done by typing about:config in the address bar.Just change "general.useragent.vendor" to a blank line if there is anything in it.

Just about to try that now....

I know in Gutsy, you had to change that string from Ubuntu to Firefox, so worth a shot on leaving it blank to see if it works.

---

### Post by robelliott2125 on 2008-08-21
bartos

I love you dude/tte!!!

I removed the value "Firefox" from the general.useragent.vendor string, and it works perfectly!!!

Thank you!!!

---

### Post by stchman on 2008-08-21
> **Slug71 said:**
> Anybody else having issues when you log into Hotmail and it asks you to upgrade your version of Firefox even though you have the latest installed?

I get that once in a great while.  Simply restart Firefox and it is back to normal.

---

### Post by Alnird on 2008-08-31
All my vendors are empty (hihi) but I still get the suggestion about upgrading some times when I logg into hotmail..

---

### Post by cgreen on 2008-09-25
Is it just me or have the Hotmail guys fixed this? Today I noticed that email address suggestions have started appearing, and I have a "switch to classic" link under my folder list. I'm running Hardy AMD64 and have not installed anything extra for Firefox...

---

### Post by bakermiller on 2008-09-25
I've had the same notice appear a few hours ago. I use FF 3.0.2. Yet it asks me to upgrade my browser to enjoy the full hotmail experience.

I was about to change the useragent fields in about:config, but then i thought i would let the stats know i am using FF in ubuntu to access my hotmail account ;)

---

### Post by bartos on 2008-09-26
> **robelliott2125 said:**
> bartos

I love you dude/tte!!!

I removed the value "Firefox" from the general.useragent.vendor string, and it works perfectly!!!

Thank you!!!

Dude thank you very much :)

---

### Post by ra2008 on 2008-10-04
thanks t worked with me as well.
i put an empty value for "general.useragent.vendor".bcoz it was Ubuntu. 
thanks

---

### Post by ra2008 on 2008-10-05
Hi

i posted in the last post that it resolved the problem.
but noow whenever i restart firefox i have to do the same steps again, i.e. go to about:config and delete the vendor

thanks

---

