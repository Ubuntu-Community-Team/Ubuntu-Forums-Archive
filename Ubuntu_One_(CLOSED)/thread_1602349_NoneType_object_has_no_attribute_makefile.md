---
title: "NoneType object has no attribute makefile"
date: 2010-10-21
forum: Ubuntu One (CLOSED)
---

### Post by deesto on 2010-10-21
I don't know whether this is happening because my machine is behind an HTTP proxy, or for some other reason.  When I enter my Ubuntu One account name and pass into "Connect to Ubuntu One" and click Connect, I get this code error instantly:
```
'NoneType' object has no attribute 'makefile'
```
If I enter nothing or invalid data into these fields, a red icon is displayed immediately, but the error above appears with valid and accurate data in the fields.

If this is a proxy issue, why doesn't the application honor the system-wide proxy settings?

---

### Post by cuby on 2010-10-27
I also have this problem and I'm behind a proxy with authentication.

---

### Post by yesint on 2010-11-03
The same for me. No idea what to do.

---

### Post by rakete on 2010-12-06
yeah, a real pain... until now I only used ubuntu one for saving some files to access them from a browser on other machines, so Dropbox is an alternative here...

but now I want to use ubuntu One to purchase Music and software from RHythmbox and the Software Center and that makes it a pain...

What a dumb error message btw. Really helpful ;)

---

### Post by duanedesign on 2010-12-08
Currently not all the pieces of Ubuntu One work behind a proxy. I would expect this to be finished in the next release.

thank you,
duanedesign

---

### Post by Teihoo on 2010-12-15
Does it completely disregard the proxy? I'm using CNTLM behind Microsoft ISA, it does help with a lot of proxy issues, but not all... Ubuntu One does not work.

---

### Post by mooobar on 2011-02-08
When does the next update come? The error still appears and ... I still got to use dropbox instead of Ubuntu One..

---

### Post by cuby on 2011-02-15
End of April.

---

### Post by kleinric on 2011-03-15
<rant> 
This is quite ridiculous :( 

For one the error message could at least say, 'Sorry we cant connect to the outside world' or at least something less cryptic.

I'm sitting behind a squid proxy at varsity that requires authentication. It generally works with everything, but I use CNTLM just because I'm too lazy to retype my password for everything. 

The fact that U1 doesn't even work through CNTLM (which does the authentication already) makes it completely unusable :( I would expect that on any university and corporate network this renders a default program on Ubuntu useless... 

If it were an addon program that I installed later on, then fine, but for a default program that comes with every single Ubuntu system this is shocking for the Ubuntu brand... 

</rant>

I'm all for developing the system over time, but error messages should be clear and the obvious use cases should surely be covered. :confused:

---

### Post by cuby on 2011-03-21
check out this bug:
[https://bugs.launchpad.net/ubuntuone-client/+bug/387308](https://bugs.launchpad.net/ubuntuone-client/+bug/387308)
you can make some noise over there...

---

### Post by deesto on 2011-04-28
Just upgraded to Natty ... and this STILL HAS NOT BEEN FIXED!!  Holy $#!+ ... That's beyond ridiculous.

---

### Post by yesint on 2011-04-30
Devs are too busy with bells and whistles. This is very sad because this is a severe bug, which affects all corporate and academic users.

---

### Post by rayhaan on 2011-04-30
yes it is rather disappointing...hopefully it is sorted soon-ish...

---

### Post by digerati on 2011-06-14
I take it this is still broken? I can't use Dropbox or Ubuntu One on my corporate network. This really sucks.

---

### Post by Ratzian on 2011-08-17
This sucks! I can't use UbuntuOne from work :(

What other alternatives are there to UbuntuOne when using auth? It seems like dropbox doesn't work either...

---

### Post by diom on 2011-10-18
Same thing here. Just installed this on my corporate XP box and got that very cryptic message. I read the first post and I figured "okay well let's see when the next release is... what? December 2010 this post... whu?"

Or something roughly along those lines.

---

### Post by kabads on 2011-10-31
I am also getting this bug - not impressed that it's been around since 2010 and will consider my membership of ubuntu one dead if it's not fixed in the near future. I wonder what spideroak are doing recently?

---

### Post by cirobr on 2012-01-02
Same here when installing UbuntuOne for Windows on a WinXP machibe.

---

### Post by hopwon on 2012-02-22
Good job I checked out this forum. I was just about to sign up for One Music but thought I'd better check before putting my CC details in.
Ubuntu development, take note: - This bug is now hitting you in the pocket!

---

