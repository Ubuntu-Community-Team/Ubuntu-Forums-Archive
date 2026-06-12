---
title: "Trac / Subversion problem"
date: 2005-06-16
forum: Server Platforms
---

### Post by casualtie on 2005-06-16
I've installed Subversion and Trac with the apt-get tool.
And I ran trac-admin to make a project.
Then I got a prompt about the "absolute path to the project Subversion repository".
What's this?
And where is it located?

-Thank you for any input

---

### Post by alastair on 2005-06-16
Before using/configuring Trac, I suspect you need to have a working subversion (svn) repository. Set svn up and check it works. Then configure Trac.

---

### Post by lgoss007 on 2005-06-17
I'm working on setting up the same thing (trac/subversion). You should be able to set up trac after setting up a subversion repository as mentioned above.

But have you figured out the apache part? I get an error in the browser:
> Missing environment variable "TRAC_ENV".

I have the SetEnv command in apache, but I can't seem to find the mod_env module in apache or Ubuntu. Is anyone running mod_env with apache2? Thanks.

---

### Post by neouser99 on 2007-11-06
You didn't happen to find a fix for this did you? I think that I have run into the same problem and fear that something is messed up with the apache installation right out of the box.

Not sure if it is apache, mod_env, or fastcgi :/

-neo

---

### Post by lgoss007 on 2007-11-07
Well somehow I got it to work, but I don't remember how, it's been awhile. It had to do with how I was setting up Apache, but you can also get that error by missing some variables Trac needs.

I just tried a few different setups from different sites, and found one that finally worked. I'd look at these for reference:

[http://trac.edgewall.org/wiki/TracOnUbuntu]("http://trac.edgewall.org/wiki/TracOnUbuntu")
[http://www.gentoo-wiki.com/HOWTO_Trac]("http://www.gentoo-wiki.com/HOWTO_Trac")
[http://philipatswarchy.wordpress.com/2006/12/17/how-to-install-trac-on-ubuntu/]("http://philipatswarchy.wordpress.com/2006/12/17/how-to-install-trac-on-ubuntu/")

The first link might help if you haven't been there already. Hope that helps.

lucas

---

