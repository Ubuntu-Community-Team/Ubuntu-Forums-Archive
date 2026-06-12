---
title: "Problems in Installtion"
date: 2007-06-13
forum: Sun Sparc Users
---

### Post by manjeetchayel on 2007-06-13
[B]Hi

I have sun blade 150. 
Can have both ubuntu and solaris on the same machine.. 
If yes.. what should i install first... 

I am tryin to install Ubuntu 6.06 LTS ( Dapper Drake)

when i tried to run the ubuntu installation i get errors such as

Illegal instruction

and 

Stack underflow 

Plz help... and where shld i add the ide=nodma string

and how do i zero the hard disk.. can i zero the harddisk and install solaris first ... as i need it urgently on my machine... But when i try to install Solaris 10.. i get error
as
>Unformatted disk
>Hardware failure

(wat could be done)

Plz help soon....[/B]

---

### Post by Delta_Farce on 2007-06-15
Hi,

You might a linux live cd that can zero your drive using dd, but I took mine out of the Blade and zeroed it using a pc (it's just an ide drive).

The illegal instruction and stack underflow might be related to your OBP version, or the amound/configuration of your RAM. Have a look through the threads here for more information on that.

You add the ide=nodma string to the boot command you use to boot the linux install cd. At the ok> prompt type 'install (or whatever option you want) ide=nodma'

I'm not sure about dual booting Solaris and Linux sorry, maybe someone else knows the answer to that?

Cheers,

Mark

---

