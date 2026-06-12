---
title: "Bulk Email Newsletter"
date: 2011-02-08
forum: Server Platforms
---

### Post by viperce on 2011-02-08
Hi I need some guidance.

I am looking for a bulk email package.I have a weekly newsletter that I would like to send to roughly around 700 parents.

I would like to setup a server Linux server that could do this for me, I would need a package that would allow me to assign mailing groups.

So i could select which groups i would like to send the newsletter to.

---

### Post by James78 on 2011-02-08
You could use PHPList for doing that. It's a webapp, where you can have subscriptions, and have people sign up and whatnot. It has a pretty big learning curve, but it's worthit. If you didn't want a webapp to do that (because you aren't really setting up a server for web stuff), I don't know what your options would be then (I'm sure someone will come along and help you in that regard). And as for sending actual email, you could use Postfix (that's what I use).

(Links to other Postfix guides at bottom of page)
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by tgalati4 on 2011-02-08
sugarcrm and gmail can do 100 emails per hour.

---

### Post by viperce on 2011-02-09
Thanks James I will look into PHPList now :P

---

### Post by SeijiSensei on 2011-02-09
If you just have a couple of lists, and are willing to do a little manual maintenance to add/remove recipients, you can do everything you want with simple email aliases.   Both sendmail and Postfix use an /etc/aliases file for this purpose.  

Suppose I have two lists of addresses, call them "friends" and "relatives".  You'd begin by first creating two simple text files with the addresses of each list's members.  If you create them in your /home directory, you'll be able to edit them easily.  Just put each address on a separate line in the file.

Next use sudo to edit /etc/aliases add these two lines:
```

friends:          :include:/home/me/friends
relatives:        :include:/home/me/relatives

```
replacing "me" with your username, of course. Then run "sudo newaliases" to rebuild the database files.

Now if you send to friends@localhost everyone in the first list will get a copy.  Same for relatives@localhost.  Of course, if you do this on a server that accepts mail for a domain, you can use [email]friends@example.com[/email] addresses instead.

If you use domain-based addresses, your recipients will be able to mail replies to these addresses, and their replies will also be redistributed.  If you don't want that, send your message to them with your own email address in the To/From fields, and the list address in a Bcc field to keep it hidden from the recipients.

---

