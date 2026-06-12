---
title: "fail2ban-client status ERROR  unsupported pickle protocol: 4"
date: 2015-11-23
forum: Server Platforms
---

### Post by rhandy2 on 2015-11-23
> 

#fail2ban-client status
#ERROR  unsupported pickle protocol: 4

# python -V
Python 2.7.10




How I can define lower pickle protocol?

---

### Post by Habitual on 2015-11-23
```
fail2ban-client -V | head -1
``` output please.

---

### Post by rhandy2 on 2015-11-23
Output

> 

#[COLOR=#000000][FONT=Ubuntu Mono]fail2ban-client -V | head -1[/FONT][/COLOR]
Fail2Ban v0.9.3



---

### Post by Habitual on 2015-11-23
Thanks, but sorry.
I don't know the pickle protocol nor that version of fail2ban.
[http://www.fail2ban.org/wiki/index.php/ChangeLog](http://www.fail2ban.org/wiki/index.php/ChangeLog) mentions cPickle, but that's all I found for this issue.

Are you using [c]Pickle on your system?
Is fail2ban grokking some pickle log?
Is a fail2ban jail using a pickle port/protocol?

---

### Post by rhandy2 on 2015-11-23
Hello

I import cPickle.

Fail2ban server runs without issues, and I dont found any pickle log for fail2ban-client.

---

### Post by rhandy2 on 2015-11-23
I found this thread h[ttps://forums.gentoo.org/viewtopic-t-990656-view-next.html?sid=ab249b0bf92ef6e79f8424d35abb2f52]("https://forums.gentoo.org/viewtopic-t-990656-view-next.html?sid=ab249b0bf92ef6e79f8424d35abb2f52")

But I dont Understand

I have 2 python versions installed

> # python3 -V
Python 3.4.3+
# python -V
Python 2.7.10




---

### Post by Habitual on 2015-11-23
> **rhandy2 said:**
> I import cPickle.
I don't know what that means or what's involved, or how it affects fail2ban.

I don't know what to make of it.
I have 2 versions of python on my desktop system.

Are you able to re(start) fail2ban successfully?
What does the /var/log/fail2ban.log say about it?

Does ```
fail2ban-client status ssh
``` give the same error?

---

### Post by rhandy2 on 2015-11-24
If I use

> #service fail2ban restart

Fail2ban restart without any error.


if I check status
> 
#fail2ban-client status ssh
ERROR  unsupported pickle protocol: 4




---

### Post by Habitual on 2015-11-24
What is involved in the "import cPickle" that you mentioned?
Imported where? how is that done?

Do you need it? Can cPickle it be removed, or unimported?

---

### Post by rhandy2 on 2015-11-25
First I make

> 
#python import.cPickle
But doenst work

I make question on Git Hub

I have this answer

> [COLOR=#333333][FONT=Helvetica Neue]I believe your fail2ban-server and fail2ban-client run within different python versions![/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]This is strange and something is wrong, using inside virtualenv, etc?[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Because python2 supports pickle up to version 2, but default pickle protocol version in python3 is 3.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]BTW, you can start fail2ban-client (and server) using dedicated python version, also:[/FONT][/COLOR]
python2 <f2b-path>/fail2ban-client ?parameters? [COLOR=#333333][FONT=Consolas]python3 <f2b-path>/fail2ban-client ?parameters?[/FONT][/COLOR]

---

### Post by rhandy2 on 2015-11-25
Results

> 
# python3 /usr/local/bin/fail2ban-client status
Traceback (most recent call last):
  File "/usr/local/bin/fail2ban-client", line 4, in <module>
    __import__('pkg_resources').run_script('fail2ban==0.9.3', 'fail2ban-client')
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 735, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 1644, in run_script
    raise ResolutionError("No script named %r" % script_name)
pkg_resources.ResolutionError: No script named 'fail2ban-client'



# python2 /usr/local/bin/fail2ban-client status
ERROR  unsupported pickle protocol: 4




---

### Post by Habitual on 2015-11-25
Offhand. I'd say remove cPickle from the system.

---

### Post by rhandy2 on 2015-11-27
I really dont know if is one ubuntu issue or not. but please read here [https://github.com/fail2ban/fail2ban/issues/1259](https://github.com/fail2ban/fail2ban/issues/1259)

---

### Post by rhandy2 on 2015-11-27
[FONT=arial black][COLOR=#333333]Solved[/COLOR]
[COLOR=#333333]First I backup /etc/fail2ban folder[/COLOR]
[COLOR=#333333]After 
> # apt-get remove fail2ban
 #apt-get autoremove 
#apt-get install fail2ban [/COLOR]
[COLOR=#333333]Replace /etc/fail2ban[/COLOR][/FONT]

---

### Post by Habitual on 2015-11-27
Glad it worked out!

FWIW:
running these on binaries is not necessary:
```
python3 /usr/local/bin/fail2ban-client status
python2 /usr/local/bin/fail2ban-client status
```

It's just
```
/usr/local/bin/fail2ban-client status
```

---

