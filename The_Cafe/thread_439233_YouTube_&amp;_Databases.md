---
title: "YouTube &amp; Databases"
date: 2007-05-10
forum: The Cafe
---

### Post by the ev on 2007-05-10
I know this question isn't really Ubuntu related (though I might be hosting the site on a linux server, so there's something), but I've a question about a site I'm going to be working on.

Basically, I'm curious to know how video and user uploaded content works with databases, rather like what YouTube does.  Can databases (MySQL and the like) actually store video in them? Would it make sense to use a database for a site like that? 

I know that's a little bit of a vague question, so here's my situation.  I used to develop websites, like 5 years ago, for small-time local businesses and the like, and then I was off to college & I didn't keep up with it.  Now it seems like every site on the web is way more than just straight HTML.  I've signed on to help develop a Peace Studies website that revolves around user-uploaded content (predominately video, but pictures and text as well), and I'm trying to get a grasp of what technologies are involved.  I've got the appearance aspects of it down (XHTML, CSS, etc.), but I'm a little in the dark, conceptually, as to what would be involved in the backend (SQL, etc.). I'm a very quick learner, I just need an idea of what it is I need to be learning!

Sooooooo, I figured that, since there are a lot of smart and savvy people who use Linux, and that smart and savvy people tend to make web-pages like this, this would be a good place to ask.  I'm thinking that I'd need to learn PHP & MySQL to pull this off?  However, there is the possibility (my client hasn't specified where it's being hosted yet) that it will have to run on a Microsoft Server, in which case I'd have to use ASP.NET & SQL Server??  I've bought a number of books on the subject, but haven't had the time to delve into them quite yet (graduation and all), but I wanted to get my bearings first.

Thanks for the help!!

---

### Post by compmodder26 on 2007-05-10
It is certainly possible to store binary content (e.g. videos) in a database.  However, that isn't really the most efficient way to go about it.  I personally prefer to store any binary files in the filesystem like normal and just include a pointer to the file's location in the database.

If you are developing on a MS platform, chances are, you'll most likely need to develop in ASP and SQL Server.  However, Apache/PHP/MySQL all have windows versions.

---

### Post by the ev on 2007-05-10
> **compmodder26 said:**
> It is certainly possible to store binary content (e.g. videos) in a database.  However, that isn't really the most efficient way to go about it.  I personally prefer to store any binary files in the filesystem like normal and just include a pointer to the file's location in the database.

I was thinking that that would be a more sensible way to go about it.  But would that still be the most reasonable approach to a system with user-uploaded content (I suppose I'm primarily concerned with directory structuring)?

And I just heard back from my clients talking with their ITS department, who inform them (not me) that their servers would not be able to run PHP.  I haven't talked to them myself, so I don't know why they couldn't.  Thanks for the reply.

---

### Post by Polygon on 2007-05-11
hmm, although i know little about this topic (databases), but i assume that they have the location of the video file in the database...

so instead of having the actual file in the database, they just have a table that lists the file name and where its located on the hard disk, and when you open up a youtube page it loads the video file from the location that its in the database..

and PHP is open source and does run on windows. Microsoft themselfs have made a deal with Zend (the company that is behind php) to help zend make PHP run faster and better on windows servers so that they can compete with linux servers.

so..... the reason they cant run php on their servers is just because its not isntalled ;)

---

### Post by DoctorMO on 2007-05-11
If I was going to do it I'd stick all the video content on a huge server farm and have the database on a completely different machine, you don't even need to link it in the database since your server farm will serve up the right video given your database record id.

nothing to it since it's the client that makes the request to link in the swf file.

---

### Post by jfinkels on 2007-05-11
Not able to run PHP? What? I agree, that just means they're too lazy to install it haha.

I would say, store actual video data to the filesystem and use the database entries to point to the files in the filesystem.

PHP is a fabulous language: it is extremely well-documented ([http://www.php.net/)](http://www.php.net/)), very easy to learn and use, and has libraries for pretty much anything.

---

### Post by argie on 2007-05-11
I think YouTube does just that. If you look at the source of the YouTube page you can figure out the link to the flv.

---

### Post by drfalkor on 2007-05-11
I belive YouTube also uses Python to handle some database stuff, arrange videos move etc.. I dont know.. but I think I read that somewhere, not sure :P

---

