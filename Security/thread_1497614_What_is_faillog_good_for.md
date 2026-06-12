---
title: "What is faillog good for?"
date: 2010-05-30
forum: Security
---

### Post by holocene on 2010-05-30
My objective was to begin monitoring attempts to logon, either remotely or at the console.

I read that the command faillog would do the trick; telling me about failed attempts and did a quick man faillog. 

I immediately did a faillog, which did not result in output. 

I did a faillog -a which essentially listed a bunch of system users, all dated 12/31/1969. 

Then I logged out and made two login attempts with bad passwords. Then logged in and did a faillog, which resulted in no output. 

I was also surprised to see that the /var/log/faillog file was dated a week ago, even though I use the system every day.

My questions:
1. Is faillog the tool to monitor failed logins?
2. Why did a failed login attempt not show?
3. Why does faillog -a show 1969 dates? 
4. Why is the file dated a week ago?

Best Regards
Steve. 


ps This is the second attempt to post a thread.

---

### Post by cariboo on 2010-05-31
Try:

```
lastb
```

This will list the failed logins.

```
last
```

will show all the logins.

---

### Post by holocene on 2010-05-31
Ok. Did some research as I should have done before posting. :redface:

According to this faillog tutorial: [http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/), I should add this line
```

auth  required pam_tally.so per_user magic_root onerr=fail
```to the top of file /etc/pam.d/comm-auth, which I did.

Then, I wanted to test limiting login failures to 3 with a sixty second timeout so I entered:

```
sudo faillog -u usrtotrash -m 3 -l 60
```where the usrname is usrtotrash, which I setup to test this scenario.

Then, I exit my acct and switched to the usrtotrash and made four or more unsuccessful attempt to login, all indicated authentication failure in the gnome login screen.

Switching back* to me, I ran faillog usrtotrash and saw:

Login       Failures Maximum Latest                   On
usrtotrash       0        3   12/31/69 18:00:00 -0600   [60s lock]


[COLOR=Red]Note that failures shows zero, when at least 3 happened. Plus, the user was not locked out that I could tell.[/COLOR]

And what is really strange, I notice that two of my other users now appear with correct dates (not 1969) like

Login       Failures Maximum Latest                   On
holocene        1        0   05/30/10 23:34:23 -0500  unknown



I am not sure what I am doing wrong. Anyone know?

Thanks.

ps
*The admin account for sudo purposes was locked out! At least, I got repeated authentication failures. I had to undo the changes to common-auth to get back in. Thank goodness I could or I would be in a fix.

---

### Post by holocene on 2010-05-31
> **cariboo907 said:**
> Try:

```
lastb
```This will list the failed logins.

```
last
```will show all the logins.

Very nice and it really suits my original objective. 

However, I am still perplexed by faillog. 

Thanks for the reply
Steve.

---

### Post by holocene on 2010-05-31
bump

anyone know how to get faillog working in lucid?

---

