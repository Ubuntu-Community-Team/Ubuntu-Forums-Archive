---
title: "New: Ubuntuzilla now includes 32bit and 64bit builds!"
date: 2012-01-06
forum: Ubuntuzilla
---

### Post by nanotube on 2012-01-06
It has been a long time in coming... but the day is finally here. Ubuntuzilla now includes both 32bit and 64bit builds of all three major mozilla package releases (those being Firefox, Thunderbird, and Seamonkey).

It appears that official ubuntu repositories are bent on lagging behind on new mozilla releases, so for the foreseeable future, Ubuntuzilla will continue to provide the latest mozilla software releases.

(And in case anyone is wondering - yes, that means I am now running a 64bit ubuntu because I got a new machine, so I finally had to scratch that 64bit itch. :) ).

Thank you all for sticking around, and coming along for the ride!

---

### Post by lovinglinux on 2012-01-20
Good to know. Welcome back.

---

### Post by nanotube on 2012-01-22
> **lovinglinux said:**
> Good to know. Welcome back.

thanks amigo - good to see you're still around as well. :)

---

### Post by kyfho23 on 2012-02-11
And I'm on a 64-bit system. Anything I need to do differently?:confused:

---

### Post by nanotube on 2012-02-12
> **kyfho23 said:**
> And I'm on a 64-bit system. Anything I need to do differently?:confused:

no, your system will automatically pull 64bit builds. (note there's currently a bug on the sourceforge file servers, see notice in red on ubuntuzilla website, next to instructions for setting up.)

---

### Post by nishant1234 on 2012-12-27
can anybody tell me more about ubuntuzilla....

---

### Post by nanotube on 2012-12-28
> **nishant1234 said:**
> can anybody tell me more about ubuntuzilla....

Hey
It is an apt repository which keeps track of the latest official mozilla builds of firefox, thunderbird, and seamonkey.

More details on project site, [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by dhdurgee on 2013-07-10
I just became aware that ubuntuzilla now supports x64 builds.  I have to this point been using Joe Lesko's builds from:

 [https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev](https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev)

But it appears that he is now having problems building and may be discontinuing his PPA.  Are your x64 builds compatible with his for install on natty and precise based distros?  If so, I am going to consider installing your newer software.

Dave

---

### Post by nanotube on 2013-07-11
> **dhdurgee said:**
> I just became aware that ubuntuzilla now supports x64 builds.  I have to this point been using Joe Lesko's builds from:

 [https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev](https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev)

But it appears that he is now having problems building and may be discontinuing his PPA.  Are your x64 builds compatible with his for install on natty and precise based distros?  If so, I am going to consider installing your newer software.

Dave

Hi Dave,

Yes, it's had the 64bit seamonkey for a while now :) Not sure what directory structures and stuff Joe's build uses (i.e., where it stuffs the installed files) - it's probably best to uninstall Joe's stuff before installing the seamonkey package from ubuntuzilla. Besides that, it should be the same - after all we are using the same code. 

With ubuntuzilla, I'm just repackaging the official seamonkey binary builds, so should be able to continue without any problems, as long as the seamonkey project keeps making binary releases. Feel free to point ubuntuzilla out to Joe, if he wants to start using it too. :)

---

