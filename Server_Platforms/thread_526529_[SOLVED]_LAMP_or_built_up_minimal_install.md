---
title: "[SOLVED] LAMP or built up minimal install?"
date: 2007-08-15
forum: Server Platforms
---

### Post by southernman on 2007-08-15
Is it better for a production environment to do a server setup using LAMP, or would it not be best to install the minimal command line system and add each component on to that? I ask as it seems to me that a LAMP is more geared toward a development platform and / or service only on a home network.

I may be way off base on that, the 10's of dozens of sites I've read through probably have the mind in check... if not checkmate.

Would it be better / preferred to use Dapper or Feisty? I am leaning toward Dapper since it's supported until 2011, where as Feisty only until 2008.

---

### Post by rbprogrammer on 2007-08-15
> **southernman said:**
> 
Would it be better / preferred to use Dapper or Feisty? I am leaning toward Dapper since it's supported until 2011, where as Feisty only until 2008.


in my opinion, that would depend on your ability.  i have a server myself, and even though i have been using linux (kubuntu in particular) for almost two years i use feisty for the server, i still consider myself to be a newbie.

since my server is not used for heavy traffic (used only by me and maybe someone else) i used feisty.  i do this so that i can learn more about apache2, and other web/ftp/ssh/print server type things.

now on the other hand, i would think if your pretty good at linux and web servering, then dapper would probably be the better choice.

---

### Post by EndPerform on 2007-08-15
LAMP should be fine for a production environment, but if you like knowing exactly what you're going to have running, starting with a baseline system would be best.  I don't think that a LAMP install does any special configuration, it just installs the pieces at once.  I'd still review the settings yourself before putting it into production either way.

If you're looking for LTS, Dapper is the way to go, but the packages are a bit older.  On the other hand, Feisty is more up to date, but loses support in 08 as you mentioned.  Personally, I keep my server up to date with the release Ubuntu is on, but it's really up to you which way you want to go.

---

### Post by az on 2007-08-15
To install LAMP is exactly the same as if you installed the base system and then ran

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

There is nothing else added.

---

### Post by foxylad on 2007-08-15
For a production system, I'd strongly reccomend using Dapper (6.06 LTS). Moving apps to a new server is something you want to do as infrequently as possible, and LTS means you don't have to do it for 5 years. Within that time you (should) be replacing the hardware anyway, which makes it much easier to migrate to the next version of Ubuntu LTS.

---

### Post by southernman on 2007-08-19
Thanks to the four of you. I've chosen 6.06 LTS and building piece by piece. 

Again... Thank you for your opinions.

---

