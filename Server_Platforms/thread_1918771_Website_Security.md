---
title: "Website Security"
date: 2012-02-01
forum: Server Platforms
---

### Post by 0011235813 on 2012-02-01
Hello, I work for a company called Teenific. I have the source code for their website [[www.teenific.com/index.php](www.teenific.com/index.php)], and I would like to know if there are any security holes? We've already had some problems in user permissions, hence why I'm writing this.
(see attached file)

---

### Post by sammiev on 2012-02-01
1st thing coming to mind. Why would you post that info here and do they know you are doing this? I would think any hacker would love to what's in place.

---

### Post by 0011235813 on 2012-02-01
> **sammiev said:**
> 1st thing coming to mind. Why would you post that info here and do they know you are doing this? I would think any hacker would love to what's in place.

Yes, they know. I know two of the admins personally, and we just had an issue where I was logged in as a user and could see other members IP addresses, which wasn't supposed to be.

And heck, I wouldn't try to hack them, they know my IP and of course, they have photographic and audio material of me, and are liscensed to publish it if I break their R&R.

I'm only posting it here because I know it's filled with users who know their stuff.

---

### Post by Cookieh on 2012-02-01
Firstly mate, this html should not resend IP info, but I might have missed some of the code of a very long (151) page document. However, with this many redirections and CSS+Java-script shared bond, it would be very hard to get an IP address as it would be taken out by normal procedures of ASP, AJAX or even some safety code of PHP. From what I have seen, all criminals would want to have this to completely grief this website, but there are some safety precautions which was intended for this purpose, so well done to somebody who wrote this...:)

---

### Post by lisati on 2012-02-01
Looks like they've wised up: I got a 404 error.

---

### Post by lisati on 2012-02-01
Looks like they've wised up: I got a 404 error.

edit: Correction. There's a typo in the link. Their board appears to be offline at the moment.

---

### Post by CharlesA on 2012-02-01
> **lisati said:**
> Looks like they've wised up: I got a 404 error.
The link was broken.

I don't think posting the source code for such a site is a good idea. If you need someone to audit it, there are professionals out there that can do so.

---

### Post by Cookieh on 2012-02-01
However, one major fault whilst I was running through second time was this:
```
/* MODERATION & FILTER STYLES */ 

.moderation_bar { 
    text-align: right; 
    padding: 6px 35px 6px 10px; 
    margin: 10px 0 0 0; 
} 

    .moderation_bar.with_action { 
        background-image: url(http://teenific.com/public/style_images/elegant/topic_mod_arrow.png); 
        background-repeat: no-repeat; 
        background-position: right center; 
    } 
     
#topic_mod_2 { 
    border-radius: 0; 
    -moz-border-radius: 0; 
    -webkit-border-radius: 0; 
    padding-top: 10px; 
    margin-top: -10px; 
} 

#topic_mod p { 
    padding: 7px; 
    font-size: 0.9em; 
} 

#topic_mod #forum_mod_options_menucontent { 
    text-align: left; 
} 

.filter_bar { 
    font-size: 0.8em; 
    text-align: center; 
    margin: 6px 0 0 0; 
    padding: 6px; 
} 

    .filter_bar select { 
        margin-right: 10px; 
    } 
     
    .filter_bar span.clickable { 
        display: block; 
    } 
     
```If this is not properly linked in the HTML, all of the users will see this bar, so one warning is to really not screw this bit up, otherwise everybody will have access to moderation.
One more thing, I think this 404 error came up of tpo as one of the staff has suggested or it was that the staff took it off for security purposes, but by looking at the code it is reletively safe unless they can get into the hosting server...

---

### Post by 0011235813 on 2012-02-01
> **Cookieh said:**
> Firstly mate, this html should not resend IP info, but I might have missed some of the code of a very long (151) page document. However, with this many redirections and CSS+Java-script shared bond, it would be very hard to get an IP address as it would be taken out by normal procedures of ASP, AJAX or even some safety code of PHP. From what I have seen, all criminals would want to have this to completely grief this website, but there are some safety precautions which was intended for this purpose, so well done to somebody who wrote this...:)
AJAX good, so there can't be any IP exploits. Unless someone were to input a script containing a worm or something of that nature to remove the safety precautions? I'll tell the admins to look into disabling scripts for users.
> **lisati said:**
> Looks like they've wised up: I got a 404 error.
Yes, but that can apparently be bypassed by using a proxy. 
> **lisati said:**
> Looks like they've wised up: I got a 404 error.

edit: Correction. There's a typo in the link. Their board appears to be offline at the moment.
There is no typo in the link, all the boards are currently off line at the moment as the site is still being tested by staff members and will not be available to members for another two weeks or so.
> **CharlesA said:**
> The link was broken.

I don't think posting the source code for such a site is a good idea. If you need someone to audit it, there are professionals out there that can do so.

Professional help is expensive, and the server and high-end software has already taken out a big chunk of budget. And I think it would be better for several people to view it than just one.


Thanks for the responses, I'll look into it.

---

### Post by lisati on 2012-02-01
> **0011235813 said:**
> 

There is no typo in the link, all the boards are currently off line at the moment as the site is still being tested by staff members and will not be available to members for another two weeks or so.



There *was* a typo in the link, which has since been corrected by another member of the staff.

---

### Post by 0011235813 on 2012-02-01
> **lisati said:**
> There *was* a typo in the link, which has since been corrected by another member of the staff.

[http://teenific.com/index.php](http://teenific.com/index.php)

Is the direct link. It is *identical* to the one I posted, and the URL has remained unchanged.

Since I actually work there, I can guarantee you Teenific has **not** opened officially yet. That's why I'm posting here; so we can fix security holes before the general public has access to it.

---

### Post by CharlesA on 2012-02-01
Any security holes would be on the server side, since that is where PHP is being run. I didn't see anything wrong with the HTML shown on the source of the page in question.

---

### Post by lisati on 2012-02-01
> **0011235813 said:**
> [http://teenific.com/index.php](http://teenific.com/index.php)

Is the direct link. It is *identical* to the one I posted, and the URL has remained unchanged.

Since I actually work there, I can guarantee you Teenific has **not** opened officially yet. That's why I'm posting here; so we can fix security holes before the general public has access to it.

As originally posted, the link was for to [http://teenific.com/index.php]](http://teenific.com/index.php]) - which won't work. There should be evidence in your boss's system's logs. Can we move on please?

By the way, do you have permission from your employer to post here? If it was my web site, I'd be nervous about people posting source.

---

### Post by kevinthecomputerguy on 2012-02-01
I can vouch that the original link ended in " ] " i remember having to backspace it.

---

### Post by lisati on 2012-02-01
> **kevinthecomputerguy said:**
> I can vouch that the original link ended in " ] " i remember having to backspace it.

Thank you. :D

---

### Post by CharlesA on 2012-02-01
> **kevinthecomputerguy said:**
> I can vouch that the original link ended in " ] " i remember having to backspace it.
Yeah, I think it was parsed with the bracket for some reason. Fixed now though.

---

### Post by 0011235813 on 2012-02-02
> **lisati said:**
> As originally posted, the link was for to [http://teenific.com/index.php]](http://teenific.com/index.php]) - which won't work. There should be evidence in your boss's system's logs. Can we move on please?

By the way, do you have permission from your employer to post here? If it was my web site, I'd be nervous about people posting source.
I never wanted to argue on it anyway, so yeah moving on.

Since it's not the actual .php server code, and only the public HTML, there is no problem.
> **kevinthecomputerguy said:**
> I can vouch that the original link ended in " ] " i remember having to backspace it.

> **lisati said:**
> Thank you. :D
Yeah, the brackets were used as just brackets, I don't know why it got included in the link.
> **CharlesA said:**
> Yeah, I think it was parsed with the bracket for some reason. Fixed now though.

---

