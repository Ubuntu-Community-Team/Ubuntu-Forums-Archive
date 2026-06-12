---
title: "posting photo's to the web"
date: 2005-05-02
forum: The Cafe
---

### Post by Eliyahu on 2005-05-02
I'm a newbie to both ubuntu and linux in general. I just had one too many XP crashes.... 

Anyway, over all, things have gone fine. Some minor bumps in the road, but nothing too bad. I have run into two issues (see my other post for the other one) that I could use some suggestions on. When I used to use the dreaded XP and I wanted to upload pictures to a service like Shutterfly to share w/ my friends, I could just select a directory using the IE upload tool and it would upload all the pics in that directory. I've yet to find a site that offers such a service for linux. Does anyone know of one or something else I could do to share the pics easily?

Thanks,

Eliyahu

---

### Post by Eliyahu on 2005-05-03
Not a single reply? Come on?! Help me out folks.

---

### Post by saik0 on 2005-05-04
I've found [http://imageshack.us/](http://imageshack.us/) to be amazingly useful while also being..uhh..well non-evil and not requiring registration. They *do* have an opt-in registration policy if you want to keep your photos together and a couple other features. 

My problem with that is that they send an email with a link to your 'account'  that gives you  a cookie that lasts a year(ish). I'd prefer a tradional login/password....::shurg::

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=saik0]I've found [http://imageshack.us/](http://imageshack.us/) to be amazingly useful while also being..uhh..well non-evil and not requiring registration. They *do* have an opt-in registration policy if you want to keep your photos together and a couple other features. 
[/QUOTE]

I second that.

---

### Post by cdhotfire on 2005-05-04
[http://www.yousendit.com/]("http://www.yousendit.com/")

you could try that, send it to your friends, or send it to urself, and copy the website, then show to friends.

you could try

[http://gmail.google.com/gmail]("http://gmail.google.com/gmail")

wish gives you like 2 gigs of space to put stuff, is that enough?
id say so.:)

if you pm me with your email, ill give you an invite to gmail, if you wish.:wink:

Edit: lol, like everyone posted at the same time, wth?

---

### Post by oddabe19 on 2005-05-04
my roomate is in Iraq, so he's been posting pictures at [http://myphotoalbum.com/](http://myphotoalbum.com/)

he's never complained about it...

---

### Post by cdhotfire on 2005-05-04
[QUOTE=oddabe19]my roomate is in Iraq, so he's been posting pictures at [http://myphotoalbum.com/]("http://myphotoalbum.com/")

he's never complained about it...[/QUOTE]

nice place, goes into bookmarks.:)

---

### Post by ProfBib on 2006-01-18
I'm working on solving dependency issues for an easy upload tool for LINUX that Shutterfly provides on its website.  Only the RPM is available, though there is a dead link to source (maybe I will send an email to their support staff and ask for a copy of that).  I've used Alien to make a Debian package and I believe that I've cleared up all the dependency issues save one:

libstdc++-libc6.1-1.so.2

I know this library is in the libstdc++2.9-glibc2.1 libraries package, but I haven't gotten around to grabbing it from the Debian archives yet (it doesn't show up in the repositories under oldlibs for some reason).  If anyone else has some insights about this, please reply.

I will keep you (and everyone else) posted.  Shutterfly is arguably one of the most polished full-featured photo-sharing websites and it would be nice to have an upload tool to simplify the task of posting all those photos of the little one for our family in France.

Best,
Evan

PS - If you're looking for a "big-name" site that allows you to upload large amounts of photos easily, you could also check out Yahoo! Photos: they have a Firefox/Linux tool that allows you to drag and drop files right from the desktop onto an area in the browser for easy upload.  The only big drawback to this service is that they do not allow you to download the hi-res images that you may have uploaded, though there is a (unofficial) workaround for this problem.

[QUOTE=Eliyahu]I'm a newbie to both ubuntu and linux in general. I just had one too many XP crashes.... 

Anyway, over all, things have gone fine. Some minor bumps in the road, but nothing too bad. I have run into two issues (see my other post for the other one) that I could use some suggestions on. When I used to use the dreaded XP and I wanted to upload pictures to a service like Shutterfly to share w/ my friends, I could just select a directory using the IE upload tool and it would upload all the pics in that directory. I've yet to find a site that offers such a service for linux. Does anyone know of one or something else I could do to share the pics easily?

Thanks,

Eliyahu[/QUOTE]

---

### Post by ProfBib on 2006-01-18
I've just run across another reference to this same problem.  It is located at this thread:

[http://www.ubuntuforums.org/showthread.php?t=44497](http://www.ubuntuforums.org/showthread.php?t=44497)

---

### Post by ProfBib on 2006-01-18
Well, it worked!  The Shutterlfy SmartUpload software is up and running.  I was able to drag and drop photos into it without a problem, but thus far the upload keeps failing.  I will wait until tomorrow morning and try again: perhaps uploading via the SmartUpload tool is down right now.  The app IS definitely communicating with the Shutterfly website though, because the new album name that I selected is displayed along with the others in my account.

---

### Post by ProfBib on 2006-01-19
Here's an update.  I was able to upload a couple of images using the software tool, but the connection to the Shutterfly servers keeps timing out.  I'm not sure if they've modified their api since this was written (probably), but I will send an email to see if they will either repair that part of the code or release the source so that it may be modified.

[QUOTE=ProfBib]Well, it worked!  The Shutterlfy SmartUpload software is up and running.  I was able to drag and drop photos into it without a problem, but thus far the upload keeps failing.  I will wait until tomorrow morning and try again: perhaps uploading via the SmartUpload tool is down right now.  The app IS definitely communicating with the Shutterfly website though, because the new album name that I selected is displayed along with the others in my account.[/QUOTE]

---

### Post by ProfBib on 2006-09-04
I have abandoned this project in favor of using the new Linux version of Google's Picasa (see Google Labs).  I would, of course, prefer to avoid proprietary code, but the Shutterfly code was, too, so might as well go with the better software.

---

