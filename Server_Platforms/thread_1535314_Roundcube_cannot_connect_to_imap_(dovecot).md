---
title: "Roundcube cannot connect to imap (dovecot)"
date: 2010-07-20
forum: Server Platforms
---

### Post by Yeti595 on 2010-07-20
Hello there,

Are there any roundcube user here ?

I have a problem connecting my roundcube to my imap server.
So, here it is :
I have a working imap server (dovecot), installed following the guide provided here [https://help.ubuntu.com/community/POP3Aggregator]("https://help.ubuntu.com/community/POP3Aggregator"). I can successfully telnet it, or ssl it (from localhost or from another ip of my local network). I can even use my thunderbird from another local computer. Well, for me it is working fine.


Then I installed roundcube (0.3.1-3) with synaptic, but I cannot connect to my localhost imap server.

I have set auth as plain ([COLOR="SeaGreen"]$rcmail_config['imap_auth_type'] = 'plain';[/COLOR])

Looking in my dovecot log, i see two different behaviour. One is when it seems correct, and roundcube log in imap server, but is disconnect immediately :

[COLOR="Magenta"]2010-07-20 21:36:00 auth(default): Info: passwd-file(mylogin,127.0.0.1): lookup: user=mylogin file=/etc/dovecot/passwd
2010-07-20 21:36:00 auth(default): Info: master out: USER 6 mylogin uid=8 gid=8 home=/var/mail/mylogin
2010-07-20 21:36:00 imap-login: Info: Login: user=<mylogin>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
2010-07-20 21:36:00 IMAP(mylogin): Info: Disconnected: Logged out bytes=39/431[/COLOR]

Second is when server is refusing the password :

[COLOR="Magenta"]2010-07-20 21:36:37 auth(default): Info: passwd-file(mylogin,127.0.0.1): lookup: user=mylogin file=/etc/dovecot/passwd
2010-07-20 21:36:37 auth(default): Info: passwd-file(mylogin,127.0.0.1): Password mismatch
2010-07-20 21:36:37 auth(default): Info: passwd-file(mylogin,127.0.0.1): PLAIN(b&#65533;&#65533;xHy&#65533;&#65533;&#65533;+bp&#65533;) != 'mypass_in_clear'
[/COLOR]

I am working with a plain text passwd, with no encryption at all. Does roundcube encrypt the password I type before to sent it to imap ? 

I cannot explain the first behaviour, when roundcube sometimes managed to connect but disconnect immediately. I manage ONE time to reach my mailboxes, but i don't know how, and this never happens again.

Thanks in advance, if anybody has any clues about my problem...

---

### Post by Yeti595 on 2010-07-20
Finally I found the solution !

Setting [COLOR="SeaGreen"]$rcmail_config['debug_level'] = 4;[/COLOR] (=show) was enough to show me the right trace on screen :

[COLOR="Red"]Warning: mcrypt_generic_init(): Iv size incorrect; supplied length: 13, needed: 8 in /usr/share/roundcube/program/include/rcmail.php on line 995[/COLOR]

Actually, the length used in mcrypt is random. But roundcube works only with the length of 8. That's why sometimes, when I am lucky, mcrypt supply a 8 length and roundcube is happy and let me in (that explains my one successful attempt).

By the way, the issue is known : [#1486307 (Roundcube freezes trying to open message) ? Roundcube Webmail](http://trac.roundcube.net/ticket/1486307)
and i solved my problem by setting [COLOR="Blue"]mbstring.func_overload = 0[/COLOR]
in my php.ini

(there is a new problem for egroupware because he needs to work with =7)

---

