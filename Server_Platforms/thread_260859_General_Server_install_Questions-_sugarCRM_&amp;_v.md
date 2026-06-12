---
title: "General Server install Questions- sugarCRM &amp; vTiger"
date: 2006-09-19
forum: Server Platforms
---

### Post by Scunizi on 2006-09-19
I've been considering installing Apache, MySQL & PHP on a machine in my home office for SugarCRM or vTiger and have several questions about the LAMP install.

If I install it on a pre-existing Dapper install will it eliminate the normal desktop GUI?

Will they server provide services for my 4 machines behind a router when the server itself is also behind the same router?  Would I access it via ip address since it won't have an official www address?

[vTiger]("http://www.vtiger.com/index.php") offers 3 unique downloads one being a .bin download as an option to install everything at one time ie MySQL, PHP & Apache & vTiger, all of which are avialable, except vTiger, through Synaptic.  They don't state which versions of the programs they have in the .bin but  they do say vTiger requires a minimum of Apache 2.0.40, MySQL 4.1.x through 5.1.x & PHP 5.0.x through 5.1.x...  Since Ubuntu can be a little "different" when it comes to insallation of genericically compiled programs, would I be better off installing these three via Synaptic and just grabbing the php files from vTiger?

My ultimate goal is to rid myself as much as possible from WinXP and ACT! while giving my wife and I the seamless ability to share a common client database.

Anyone know both sugarCRM & vTiger to express an opinion on which they prefer and why?  Including the ability to add or change custom fields to tailor the programs to a specific industry?

Being a budding nOOb with almost 4 whole months experience w/Ubuntu and Linux, I tend to want the path of least resistance.  However, I do have an extra machine I can use to play with without having to worry about mucking something up on one of the other 4 I have running.  For testing it would be fine, but I'd get resistance from my better half having yet another computer hooked up and sucking juice.:rolleyes: 

Thanks for your responses!

---

### Post by ff2k on 2006-09-20
> **Scunizi said:**
> If I install it on a pre-existing Dapper install will it eliminate the normal desktop GUI?


AFAIK, it won't be affected. I have a similar setup at home where I have a desktop and running AMP without problems.

> **Scunizi said:**
> Will they server provide services for my 4 machines behind a router when the server itself is also behind the same router?  Would I access it via ip address since it won't have an official www address?


Either you use an IP address or enter a host entry in the /etc/hosts file so you can use a regular "internal.mycrm" url. If you want to access it behind a firewall, you may need to map the incoming port to forward it to your LAMP Desktop.


> **Scunizi said:**
> [vTiger]("http://www.vtiger.com/index.php") offers 3 unique downloads one being a .bin download as an option to install everything at one time ie MySQL, PHP & Apache & vTiger, all of which are avialable, except vTiger, through Synaptic.  They don't state which versions of the programs they have in the .bin but  they do say vTiger requires a minimum of Apache 2.0.40, MySQL 4.1.x through 5.1.x & PHP 5.0.x through 5.1.x...  Since Ubuntu can be a little "different" when it comes to insallation of genericically compiled programs, would I be better off installing these three via Synaptic and just grabbing the php files from vTiger?


Both CRM will work fine if you just download the PHP files. Both can still work with php4 and php5.

> **Scunizi said:**
> Anyone know both sugarCRM & vTiger to express an opinion on which they prefer and why?  Including the ability to add or change custom fields to tailor the programs to a specific industry?


I tried both and I find the latest stabe vtiger (4.x) to be a lot faster then sugar. There's a big debate about vtiger ripping off sugar.

> **Scunizi said:**
> Being a budding nOOb with almost 4 whole months experience w/Ubuntu and Linux, I tend to want the path of least resistance.  However, I do have an extra machine I can use to play with without having to worry about mucking something up on one of the other 4 I have running.  For testing it would be fine, but I'd get resistance from my better half having yet another computer hooked up and sucking juice.:rolleyes: 

Thanks for your responses!

Oh I would definately recommend playing around first with the spare machine. That's where you do your "what ifs" and you won't feel bad if you screw it up.

---

### Post by Scunizi on 2006-09-20
ff2k... Thanks for your replies.  It's kinda what I figured but just needed to verify my gut instinct.  vTiger has just released a new version 5.x in case you're using it.

Can you tell me if it's fairly easy to add and delete fields?  My wife is a long time loan officer and I'm a Realtor sharing the same leads and referral clients.  I'm also putting together something to help families with their computers in my local area as a segway to introduce Ubuntu or simply to cleanup their old machines.

I've been debating if I should use one of the CRM packages I mentioned or build something from OpenOffice's Base.  Any thoughts?

---

### Post by ff2k on 2006-09-20
You can't delete fields but you can disable them. I haven't used vTiger extensively as I only installed it for our Sales team. Sorry.

I don't have experience in OO as well. Sorry! :(

---

