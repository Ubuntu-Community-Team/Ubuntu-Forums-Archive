---
title: "Postfix:Is it possible to rewrite sender address only for selective recipient?"
date: 2006-08-13
forum: Server Platforms
---

### Post by Akhran on 2006-08-13
In my mail.cf, I have ```
sender_canonical_maps = hash:/etc/postfix/sender_canonical
```
In my /etc/postfix/sender_canonical, I have ```
@originaldomain.com @rewrittendomain.com
```

When I send out email with [email]testuser@originaldomain.com[/email] as the sender, I receive it as [email]testuser@rewrittendomain.com[/email].

Is it possible to configure such that the rewritting of address takes effect only when sending to a particular recipient?

Thanks !

---

### Post by MJN on 2006-08-15
Okay, firstly this may not be the best solution or even a solution at all...! It's just that I had to implement a 'per specific destination' configuration (in order to force 7-bit encoding for some recipients) and so a variation on my solution could well work for you.

I don't want to imply I'm an 'expert' in all of this - I just learnt enough to achieve what I wanted to do... Hence, I will show you my relevent config verbatim then you can change it, and yours, to suit. 

Firstly, in /etc/master.cf I added the following line (leaving the default **smtp** service line alone):

```
no8bitmimesmtp      unix  -       -       -       -       -       smtp -o smtp_never_send_ehlo=yes
``` 
Hence, in my case, this set up a service (callable by **no8bitmimesmtp** - you call yours something suitable) which simply runs the smtp dameon with the **smtp_never_send_ehlo=yes** directive set (i.e. all over config remains the same). In your case you'd need to instead force the **sender_cananonical_maps...** directive.

Now, this 'modified' service needs to be called on a per-destination basis and this is done using a transport table. So, in /etc/postfix/transport I added the following:

```
orange.net              no8bitmimesmtp:[smtp.blueyonder.co.uk]
``` 
This meant that all mail to **orange.net** would be 'ran through' the special no8bitmimesmtp service (with **smtp.blueyonder.co.uk** set as the next hop - modify to suit or check the check out the **transport** manpage to see how to modify accordingly and do more-specific/fancy matching etc).

After creating/modifying /etc/postfix/transport create the database version using postmap (which I'm guessing you're familiar with).

Then, finally(!), in **/etc/postfix/main.cf**, I added the following line:

```
transport_maps = hash:/etc/postfix/transport
``` 
..to check the above transport table for matches (and corresponding actions).

I think that's pretty much it. If it looks like this method could be of use, and you need anything elaborating on, just shout. I've kept it brief as it could work out-of-the-box for you (modified to suit) or it could be way off target.... either way it'd be a waste to add any more detail!
;)

Mathew

---

### Post by LordHunter317 on 2006-08-15
There's no need to do that.

Just add the addresses you want rewritten:```
user@example.com user@newdomain.com
```Domain rewrites take lower priority, so you can still specify a catch-all rule and rewrite specific addresses.  

No need to be more complicated than that.

---

### Post by Akhran on 2006-08-16
Is this mapping configured in sender_canonical file? If the rewriting of the sender's address is to take place only when sending to a particular domain (eg. yourdomain.com), how does the rule differentiate when to apply the adddress rewriting?

Thanks.

> **LordHunter317 said:**
> There's no need to do that.

Just add the addresses you want rewritten:```
user@example.com user@newdomain.com
```Domain rewrites take lower priority, so you can still specify a catch-all rule and rewrite specific addresses.  

No need to be more complicated than that.

---

### Post by LordHunter317 on 2006-08-16
I'm somewhat confused?  You want to rewrite specific sender addresses specially?  Or you only want to rewrite sender addresses when the recipient is a certain person?

If it's the former, I told you what to do.  If it's the latter, you will need to setup some filtering.  MJN has the right idea, here's the authortative docs: [http://www.postfix.org/FILTER_README.html](http://www.postfix.org/FILTER_README.html)

---

### Post by LordHunter317 on 2006-08-16
Actually, MJN really has the right idea.  Filtering shouldn't be required for this. 

You'll have to specify canonical_maps to the smtpd command line though, I think.

---

### Post by Akhran on 2006-08-16
In the /etc/master.cf file, I add in 
```
mysmtp      unix  -       -       -       -       -       smtp -o sender_canonical_maps=hash:/etc/postfix/sender_canonical
``` 

However, the rewriting of the address doesn't seem to take place.

If I change it to 
```
mysmtp      unix  -       -       -       -       -       smtp -o smtp_generic_maps=hash:/etc/postfix/generic
```
the rewriting takes place.

Do you have the same problem with sender_canonical_maps table?

Thanks.




> **MJN said:**
> Okay, firstly this may not be the best solution or even a solution at all...! It's just that I had to implement a 'per specific destination' configuration (in order to force 7-bit encoding for some recipients) and so a variation on my solution could well work for you.

I don't want to imply I'm an 'expert' in all of this - I just learnt enough to achieve what I wanted to do... Hence, I will show you my relevent config verbatim then you can change it, and yours, to suit. 

Firstly, in /etc/master.cf I added the following line (leaving the default **smtp** service line alone):

```
no8bitmimesmtp      unix  -       -       -       -       -       smtp -o smtp_never_send_ehlo=yes
``` 
Hence, in my case, this set up a service (callable by **no8bitmimesmtp** - you call yours something suitable) which simply runs the smtp dameon with the **smtp_never_send_ehlo=yes** directive set (i.e. all over config remains the same). In your case you'd need to instead force the **sender_cananonical_maps...** directive.

Now, this 'modified' service needs to be called on a per-destination basis and this is done using a transport table. So, in /etc/postfix/transport I added the following:

```
orange.net              no8bitmimesmtp:[smtp.blueyonder.co.uk]
``` 
This meant that all mail to **orange.net** would be 'ran through' the special no8bitmimesmtp service (with **smtp.blueyonder.co.uk** set as the next hop - modify to suit or check the check out the **transport** manpage to see how to modify accordingly and do more-specific/fancy matching etc).

After creating/modifying /etc/postfix/transport create the database version using postmap (which I'm guessing you're familiar with).

Then, finally(!), in **/etc/postfix/main.cf**, I added the following line:

```
transport_maps = hash:/etc/postfix/transport
``` 
..to check the above transport table for matches (and corresponding actions).

I think that's pretty much it. If it looks like this method could be of use, and you need anything elaborating on, just shout. I've kept it brief as it could work out-of-the-box for you (modified to suit) or it could be way off target.... either way it'd be a waste to add any more detail!
;)

Mathew

---

