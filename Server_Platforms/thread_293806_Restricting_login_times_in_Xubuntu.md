---
title: "Restricting login times in Xubuntu"
date: 2006-11-05
forum: Server Platforms
---

### Post by EnglishRob on 2006-11-05
Hi folks,

I have setup a Xubuntu system for my step-daughter to use in her bedroom.  To stop her using the computer late and night I want to implement some sort of restrictions to when she can login.

I have had a browse of Google and asked in my local LUG mailing list and was pointed in the direction of [this](http://www.debian-administration.org/articles/227) guide.

Now I have altered the /etc/pam.d/gdm file and added the following:

```

auth     required    pam_time.so

```

and I have also added the following to /etc/security/time.conf:

```

* ; * ; !rob ; Al0000-2400

```

I thought I'd try it with my own login account first.  How I understand it everyone but the user **rob** should be able to login at any time.  I tried logging in with my step-daughters account but it came up with an error message about authentication (I think it was 'Authentication Failed').

I also tried changing the above line in time.conf to:

```

* ; * ; rob ; Al0000-2400

```

Again, this didn't seem to work.

Can anyone suggest anything?

Ta,

Rob

---

