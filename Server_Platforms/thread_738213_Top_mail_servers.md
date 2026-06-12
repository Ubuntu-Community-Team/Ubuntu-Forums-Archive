---
title: "Top mail servers"
date: 2008-03-28
forum: Server Platforms
---

### Post by aiflin on 2008-03-28
Folks,
    I am in the process of hosting a site on Tomcat on Ubuntu. I will be also running a mail server. As per your experience which are the top mail servers? While googling I came to know these names :
 
Sendmail
Postfix
 
 
I would appreciate if you can give your inputs.
 
Thanks,

---

### Post by HermanAB on 2008-03-28
Depends on what you need.  Postfix and Qmail are best in terms of handling large volumes of mail and millions of users.  Citadel is best in terms of features, ease of install and maintenance and it can handle tens of thousands of users, which may be enough for you.  Sendmail is unbeatable if you are a masochist and enjoys banging your head on your keyboard, but it can actually send mail too.

---

### Post by aiflin on 2008-03-28
Thanks Herman. 

    I am starting a new site and in a process of selecting a mail server. I have heard lot about Sendmail.

Before selectiing, I just wanted to make sure I am selecting a robust mailserver.

Also, I assuming these all mail server are free of cost, right ? As in no licensing fee for commercial use.

---

### Post by aiflin on 2008-03-28
to add,
  robust and fast mail.

---

### Post by HermanAB on 2008-03-28
They are all robust and fast.

Pick the server depending on your needs:
Millions of users: Postfix or Qmail
Tens of thousands of users plus web integration: Citadel

Sendmail however, is strictly for masochists only.  I suspect that someone suggested it as a joke.

Cheers,

Herman

---

### Post by aiflin on 2008-03-28
Thanks Herman.

Just wanted your comment on Exim and Apache James.

James is java based mail server. 

Looks like Exim and Postfix are quite famous.

---

### Post by freebeer on 2008-03-28
I have sendmail running (adequately for what I use it for), but HermanAB's dead on.  You need to be masochistic to want to use it if there are alternatives.

It took me forever to clue in that sendmail's config file had to be "compiled".  Didn't expect that and only some obscure reference led me down the path to finally realize that.

When I move to 8.04 I'm probably going to go the Citadel route (for additional reasons).

---

### Post by netlogic on 2008-03-28
> **HermanAB said:**
>   Sendmail is unbeatable if you are a masochist and enjoys banging your head on your keyboard, but it can actually send mail too.

Yea, it feels great when I drill a hole in my head.  Sendmail has some nightmarish features.

---

### Post by FakeOutdoorsman on 2008-03-28
I'm a sendmail user.  It works just fine, but I'm envious of those Postfixers.

---

### Post by HermanAB on 2008-03-28
Hmm, I got to confess - the very first mail server I used was sendmail and I actually edited the configuration file with vi.  Eventually I upgraded to Postfix and thought that I discovered email heaven.  Nowadays though, I use Citadel and really, there is no looking back.

Postfix is a drop-in replacement for sendmail and there are some things that you really need Postfix for, for example as a spam filter front-end for an existing Exchange server, but for everything else, there is Citadel.

Cheers,

Herman

---

### Post by scottro on 2008-03-28
Not that I have anything against sendmail, but I do remember a funny quote--possibly bash.org, possibly a collection from #freebsd on Undernet, but anyway.

Someone wrote
Tihs isn't working!  #%(^#(@!%(&

Someone else wrote

Please don't post your sendmail configuration in channel.  

Although from what I hear, it's there's another, more human friendly file that is used now.

---

### Post by HermanAB on 2008-03-29
Configuring sendmail is really very simple, as you can see here:
[http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/files/aixfiles/sendmail.cf.htm](http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/IBMp690/IBM/usr/share/man/info/en_US/a_doc_lib/files/aixfiles/sendmail.cf.htm)

Here is a solution to the Towers of Hannoi problem in sendmail script:
# Towers of Hanoi
S49
RHANOI:$+	$:1 2 3$1
R$-$-$-$*[$+]	$:$1$2$3$4          
R$-$-$-		$@$1$2$3 
R$-$-$-@$*	$:$>49 $1$3$2$4     
R$-$-$-$*	$:$>49 $2$3$1$4[Move Top Disk Of Peg $1 To Peg $3]      
R$-$-$-$*	$:$3$2$1@$4      

Add to your /etc/sendmail.cf equivalent.
If S49 is in use, change the three `49's to an unused ruleset.

Invoke with something like:

  echo '49 HANOI:@@@@' | /usr/sbin/sendmail -bt -d21

--

So, as you can see, there really is nothing to it...

---

### Post by farahbod on 2008-03-30
> **scottro said:**
> Not that I have anything against sendmail, but I do remember a funny quote--possibly bash.org, possibly a collection from #freebsd on Undernet, but anyway.

Someone wrote
Tihs isn't working!  #%(^#(@!%(&

Someone else wrote

Please don't post your sendmail configuration in channel.  

Although from what I hear, it's there's another, more human friendly file that is used now.

:lolflag:

I am a sendmailer too! ;)
But I will choose postix next time!
I had no experience with Citadel. Thank you Herman, I'll test it.

---

### Post by kevdog on 2008-03-30
Herman -- that post for the sendmail configuration is one in a million.  I realized it actually wasn't a joke!

---

### Post by HermanAB on 2008-03-30
Yeah, sendmail is very simple, for very high values of simple...

I can't help but wonder what developmental problem causes people to write a parser that behaves like this:

$#mailer $@host $:user

This specifies the {mailer, host, user} 3-tuple necessary to direct the mailer. If the mailer is local, the host part may be omitted. The mailer must be a single word, but the host and user may be multi-part. If the mailer is the built-in IPC mailer, the host may be a colon-separated list of hosts that are searched in order for the first working address, exactly like MX (machine exchange) records. The user is later rewritten by the mailer-specific envelope rewrite set and assigned to the $u macro. As a special case, if the value to $# is "local" and the first character of the $: value is "@", the "@" is stripped off, and a flag is set in the address descriptor that causes sendmail to not do ruleset 5 processing.

Normally, a rule that matches is retried, that is, the rule loops until it fails. An RHS may also be preceded by a $@ or a $: to change this behavior. A $@ prefix causes the ruleset to return with the remainder of the RHS as the value. A $: prefix causes the rule to terminate immediately, but the ruleset to continue; this can be used to avoid continued application of a rule. The prefix is stripped before continuing.

The $@ and $: prefixes may precede a $> spec. For example:

R$+  $: $>7 $1

matches anything, passes that to ruleset seven, and continues; the $: is necessary to avoid an infinite loop. 

Uhmm, yeah, well, no, fine...

---

### Post by freebeer on 2008-03-30
> **HermanAB said:**
> Yeah, sendmail is very simple, for very high values of simple...


[IMG]http://www.freebeer.is-a-geek.org/graphics/lmao2.gif[/IMG]

And the rest of the post was classic.  :D

---

### Post by netlogic on 2008-03-30
> **HermanAB said:**
> Yeah, sendmail is very simple
.

yea, long as you are sending the mail to yourself or outsource the entire thing. OMG OMG... What the hell am I editing...please mail go go... don't come back... oh god... other servers bouncing my servers... omg...omg... I guess I'm not going back home tonight again.

Anyway, I think most default mail server installation for most distros are now Postfix.

---

### Post by netlogic on 2008-03-30
I found a good link for people who are indecisive about their mail servers.

[http://shearer.org/MTA_Comparison](http://shearer.org/MTA_Comparison)

---

### Post by hyper_ch on 2008-03-31
I love postfix because of it's integrated anti-uce options... very easily setup ;)

---

