---
title: "Recreate a Website??"
date: 2010-09-17
forum: The Cafe
---

### Post by rfisher1134 on 2010-09-17
Hey guys,
I'm a member on another forum and the domain is expiring in a few months. The owner has been MIA for as long as I've been on there, so I don't think there is any hope in it being renewed. A lot of the members are trying to figure out a way to save or recreate it.

Does anyone know a way to copy all of the info from this site kind of like htttrack that would be able to be restored onto another domain on a dedicated server? If you have any ideas please let me know. 

P.S. I'm kind of a n00b so sorry if I said anything stupid or redundant in the post.:redface:

---

### Post by Legendary_Bibo on 2010-09-17
You could copy the html code by viewing the source (you would have to go to each main page area, and the ones that update), but that wouldn't get you the images uses, and you would have to change where the source of the files are coming from and what not.

---

### Post by CJ Master on 2010-09-17
If you could contact the owner via email (most forums require you to imput your email) you could ask about transfering ownership of the domain.

---

### Post by Barrucadu on 2010-09-17
You could check the WHOIS records for the owner's contact details. If he's not responding to emails, you could try ringing or sending a letter (WHOIS is scary sometimes).

---

### Post by Joe of loath on 2010-09-17
Can you FTP in as an anonymous user and simply copy everything? I'm not sure if many sites let you do that, you'd probably need the owner's password.

EDIT: Would rsync work?

---

### Post by Paqman on 2010-09-17
If it's a forum then the content is stored in a database (probably MySQL). You need to get a copy of that database. Bear in mind though that depending on how/where it's hosted, even the person who created the forum may not have access it. Some hosts like to keep that kind of thing to themselves, so they can charge people for access to it.

---

### Post by andreseso on 2010-09-17
Hello,

I believe wget has an option of downloading recursively a whole web site, even though it has been years since I have reviewed the man page.

I would start a new forum with similar appearance and keep it at its latest stable version and find a way of customizing this forum to show through several links the read only history of the old forum.  If you are good programming, with for example php, you can import everything from the static security copy html pages into the new forum software, with the exception of each user's password.  They would have to go through the trouble of requesting a new password.

Depending of your skills, you can resuscitate this moribund forum.

Love,
Andres

---

### Post by koenn on 2010-09-17
getting ownership of the domain and the hosting transferred to you would be easiest by far. 

other than that, I agree with paqman, and partially with andreseso : the next best thing would be to get a copy or an sql dump of the database

To totally recreate the forum you'd probably also want the forum engine's config / modifications/ addons / ...

recursive wget would probably work to get a read-only, static html copy of the website as it is now - it could be put online as a read-only archive 
I've  played with  wget to create a (static, but browsable) fall-back mirror of an important wiki, it seems to work

parsing all of those files so that you can extract all relevant data to actually recreate a working forum -- that sounds like one hell of a job.

---

### Post by pwnst*r on 2010-09-17
If you don't have access to the DB, then don't bother.  Just start something new and migrate the users.

---

### Post by rfisher1134 on 2010-09-17
I agree that getting ownership would be the easiest way to make this happen, but the owner hasn't responded to any emails or even phone calls from any of the members in years.

---

### Post by rfisher1134 on 2010-09-17
> **pwnst*r said:**
> If you don't have access to the DB, then don't bother.  Just start something new and migrate the users.

I knew it would be hard...I just wanted to see if their was any relatively "easy" way of saving the site and all of its data. Thanks everyone for your answers.

---

### Post by Brunellus on 2010-09-17
Note that doing anything without the author's consent would likely be a copyright violation, unless the content had been released on a more permissive license.  If you have serious copyright concerns, see your friendly neighborhood copyright attorney.

---

### Post by koenn on 2010-09-17
hm, yeah, copyright and stuff. completely forgot.
always good to have a lawyer around ...

---

### Post by rfisher1134 on 2010-09-17
> **Brunellus said:**
> Note that doing anything without the author's consent would likely be a copyright violation, unless the content had been released on a more permissive license.  If you have serious copyright concerns, see your friendly neighborhood copyright attorney.

Ya but would the threads be owned by the owner of the site or their authors/contributors? I understand that the logos and such would be be a copyright violation, but wouldn't the information on the forum be the property of those who created it?

---

### Post by Brunellus on 2010-09-17
> **rfisher1134 said:**
> Ya but would the threads be owned by the owner of the site or their authors/contributors? I understand that the logos and such would be be a copyright violation, but wouldn't the information on the forum be the property of those who created it?
That would depend on the terms of service.  Again, if you're looking for legal advice, the Internet is a bad place for it.

---

### Post by eriktheblu on 2010-09-17
The creator of a work automatically (in most countries) has copyright. By posting it on a forum, they typically give that forum license to use it.

The problems I can see are:
1. While that forum may have license to use those posts, it probably doesn't transfer over to 3rd parties to republish. 

2. You may not have license to use copyrighted images and code from the original site.

---

### Post by shuamu on 2010-09-18
> **pwnst*r said:**
> If you don't have access to the DB, then don't bother.  Just start something new and migrate the users.

Second that.

Your best bet would definitely be to start from scratch and make the best attempt you can to get any and all active users on the forum to switch over. If you have admin privileges on the forum, I'd suggest putting up a sticky there with the new site.

It would be easier and take less time to just start from scratch in this case.

You could borrow some aspects of the design without any kind of copyright infringement, but unless you actually buy the domain up from its defunct owner, you could get yourself into a lot of trouble... though, now that I think about it, the owner seems like they'd never come after you for it. Either way, just start fresh.

---

### Post by drawkcab on 2010-09-19
> **shuamu said:**
> Second that.

Your best bet would definitely be to start from scratch and make the best attempt you can to get any and all active users on the forum to switch over. If you have admin privileges on the forum, I'd suggest putting up a sticky there with the new site.

It would be easier and take less time to just start from scratch in this case.

You could borrow some aspects of the design without any kind of copyright infringement, but unless you actually buy the domain up from its defunct owner, you could get yourself into a lot of trouble... though, now that I think about it, the owner seems like they'd never come after you for it. Either way, just start fresh.

Also, once you migrate the users you can set up a sub forum dedicated to posting links to the most important discussions on the original forum.

---

### Post by koenn on 2010-09-19
> **drawkcab said:**
> Also, once you migrate the users you can set up a sub forum dedicated to posting links to the most important discussions on the original forum.

and how are the url's for those links going to work if the domain name expires and no longer points to the server where that forum was located ? even assuming the forum will still be there ...

---

