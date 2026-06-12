---
title: "Problem reading online mails"
date: 2008-02-19
forum: Server Platforms
---

### Post by satimis on 2008-02-19
Hi folks,


Some companies, including mine, disable the cookies on browser (I suppose) making their staffs unable to send/receive online mails other than their own.  I even can't read webmails on my own server.  I tried going through other proxy servers but without result.  Is there anyway to breakthrough this barrier?  TIA


B.R.
satimis

---

### Post by faulkes on 2008-02-19
It would be inappropriate I think for the forum to engage in or suggest attempts to bypass your companies stated security policies.

Faulkes

---

### Post by MJN on 2008-02-19
Are you sure it's a cookie issue? I would expect you to have trouble with all sorts of sites as such session-tracking is quite popular (practically all sites that require logins do so).
 
I seem to recall you are using Squirrelmail, which does indeed require cookies. Does it keep telling you you must be logged in?
 
I don't believe there is any way around it I'm afraid.
 
Mathew

---

### Post by satimis on 2008-02-19
> **faulkes said:**
> It would be inappropriate I think for the forum to engage in or suggest attempts to bypass your companies stated security policies.

I doubt whether it is security policy.  I'm free browsing Internet searching info and downloading files on websites but only unable reading webmails on Internet and login discussion forums.  I can send and receive emails via the server at work.

satimis

---

### Post by satimis on 2008-02-19
> **MJN said:**
> Are you sure it's a cookie issue? I would expect you to have trouble with all sorts of sites as such session-tracking is quite popular (practically all sites that require logins do so).
 
I seem to recall you are using Squirrelmail, which does indeed require cookies. Does it keep telling you you must be logged in?
 
I don't believe there is any way around it I'm afraid.

Hi Mathew,

The situation at work is similar to connecting my home server on proxy server, proxydom.com.  I tested proxydom.com.  I can connect my home server starting SM but unable to login.  On login it just hangs there until time out, saying "enable the cookies".  The situation is similar to my work, just hanging until timeout but w/o warning.  I can browse yahoo, gmail, ubuntuforums, etc. freely but unable to login webmail/forum.  I'm free sending/receiving emails via office server including attachment.

satimis

---

### Post by MJN on 2008-02-19
As I mentioned, I'm afraid you're screwed.
 
Have a word with your sys admin people. Chances are they won't budge (as presumably this isn't a work requirement) but there's no way around it... I'm sure some creative lateral thinkers could come up with a solution involving proxy-based browsing (where the proxy holds you cookie) but you'd be opening a can of worms with that one that I can't see it worth the effort.
 
Mathew

---

