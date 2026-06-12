---
title: "login information"
date: 2008-11-04
forum: Security
---

### Post by liung on 2008-11-04
When I login in ubuntu from local or ssh , There has a notice :

ubuntu login:
passwd:

Which file should be edit to make it like this :

ligin:
passwd:

Thanks !

---

### Post by liung on 2008-11-06
Anyone knows how to do ?

Help me !

---

### Post by brian_p on 2008-11-06
> **liung said:**
> 

Which file should be edit to make it like this :

ligin:
passwd:

Thanks !

The word 'Ubuntu' is obtained from the file /etc/hostname. You could change the file contents.

---

### Post by liung on 2008-11-08
Thanks for your help first !

But if I modify /etc/hostname to satisfy my need(that means I will let /etc/hostname file be blank) , what shoule I do to config my hostname ?

---

### Post by brian_p on 2008-11-09
> **liung said:**
> 

But if I modify /etc/hostname to satisfy my need(that means I will let /etc/hostname file be blank) , what shoule I do to config my hostname ?

You can only achieve satisfactorily what you want at source code level (I think). Making /etc/hostname blank may not work anyway without altering /etc/init.d/hostname.sh. Please see the comments in that file.

Even if you could get it to work the absence of a hostname for the machine is likely to raise problems with networking applications, mail, for example.

Why do want a login prompt without a hostname?

---

### Post by cariboo on 2008-11-09
If you have a blank hostname, you will run into problems, such as not being able to use sudo.

Why not just change the prompt in /etc/skel/.bashrc. This is the section that needs to be modified:

```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

```

Have a look here:

[http://tldp.org/HOWTO/Xterm-Title-4.html](http://tldp.org/HOWTO/Xterm-Title-4.html)

Section 4.3 bash, for what the different options are.

Jim

---

### Post by brian_p on 2008-11-09
> **cariboo907 said:**
> 

Why not just change the prompt in /etc/skel/.bashrc.

Isn't that for after logging in?

---

### Post by liung on 2008-11-09
> **brian_p said:**
> You can only achieve satisfactorily what you want at source code level (I think). Making /etc/hostname blank may not work anyway without altering /etc/init.d/hostname.sh. Please see the comments in that file.

Even if you could get it to work the absence of a hostname for the machine is likely to raise problems with networking applications, mail, for example.

Why do want a login prompt without a hostname?

Because I use telnet to login this server from other machine , I do not want others know this host's name before they login , otherwise they will know some information about the host before they login .
For redhat , if I telnet it ,there is just "login:" . And that is what I want . 
I think it shoule be code level too , but I don't know where to change in /etc/init.d/hostname.sh file . it seems too simple .

Thanks again !

---

### Post by jpkotta on 2008-11-16
I think brian_p is right.  From [http://www.kernel.org/pub/linux/libs/pam/FAQ:](http://www.kernel.org/pub/linux/libs/pam/FAQ:)

> Q7: When I upgrade to a newer version of PAM, my login prompt changes! Why?

Red Hat shipped a version of Linux-PAM that had a default PAM_USER_PROMPT
(defined in Linux-PAM-X.YY/libpam/pam_private.h as PAM_DEFAULT_PROMPT) of
"Login: ". They did this to reduce the amount of work needed to port
applications to using PAM authentication.  In the longer term, applications
should be fixed to specify their preferred user prompt with the following
line inserted before their first call to pam_authenticate():

	pam_set_item(pamh, PAM_USER_PROMPT, "Login: ");

[Instead of "Login: ", the desired prompt should be used..]

The default prompt, is more ugly: "Please enter username: ", and will remain
this way, to encourage application developers to write robust applications!

(In case you are wondering, the "official" Sun version is

	"Please enter user name: "

, which besides being ugly, is also bad UN*X-speak..!)

Another solution, if you find this behavior to be a problem, is to do the
following: upgrade to an enhanced version of the linux-utilities:

Derrick J. Brashear has contributed this:
> [ftp://ftp.dementia.org/pub/pam/util-linux-2.5-26.src.rpm](ftp://ftp.dementia.org/pub/pam/util-linux-2.5-26.src.rpm)
> has been updated but again I forgot to increment the build number.

```
apt-get source login
cd shadow-4.1.1/src
less login.c
```

```
                        /* Make the login prompt look like we want it */
                        if (!gethostname (hostn, sizeof (hostn)))
                                snprintf (loginprompt,
                                          sizeof (loginprompt),
                                          _("%s login: "), hostn);
                        else
                                snprintf (loginprompt,
                                          sizeof (loginprompt), _("login: "));

                        retcode =
                            pam_set_item (pamh, PAM_USER_PROMPT, loginprompt);
                        PAM_FAIL_CHECK;

```

---

### Post by liung on 2008-12-02
> **jpkotta said:**
> I think brian_p is right.  From [http://www.kernel.org/pub/linux/libs/pam/FAQ:](http://www.kernel.org/pub/linux/libs/pam/FAQ:)



```
apt-get source login
cd shadow-4.1.1/src
less login.c
```

```
                        /* Make the login prompt look like we want it */
                        if (!gethostname (hostn, sizeof (hostn)))
                                snprintf (loginprompt,
                                          sizeof (loginprompt),
                                          _("%s login: "), hostn);
                        else
                                snprintf (loginprompt,
                                          sizeof (loginprompt), _("login: "));

                        retcode =
                            pam_set_item (pamh, PAM_USER_PROMPT, loginprompt);
                        PAM_FAIL_CHECK;

```

It seems a little more change to do , so I just let it be . 
Thanks for all yours help !

---

