---
title: "Postfix hold all outgoing mail"
date: 2012-12-10
forum: Server Platforms
---

### Post by zer0net on 2012-12-10
Hello everyone, 

What I am trying to achieve:  
I want to put ALL outgoing emails on hold, unless they are going locally. 

What I have done so far:

in ./etc/postfix/main.cf 
... 
smtpd_recipient_restrictions =   
check_recipient_access hash:/etc/postfix/hold 
permit_mynetworks 
permit_sasl_authenticated 
reject_unauth_destination 

in ./etc/postfix/hold 
domain1.tld HOLD 
domain2.tld HOLD 
.... 

Issues I am having:
1. This does work (partially) this way seems like I have to define every domain that it should not send to, which is every domain out there, how do I make it reject every single domain except local? 

2. When the "To" or "CC" or "BCC" contain both non-local and local email addresses, full email goes into HOLD and does not get delivered to local. How do I get around that so it gets delivered to all local while the external gets held? 


Any help will be appreciated. 

Thank you all in advance

---

### Post by lisati on 2012-12-10
[https://groups.google.com/forum/?fromgroups=#!topic/mailing.postfix.users/kPyh5euz33g](https://groups.google.com/forum/?fromgroups=#!topic/mailing.postfix.users/kPyh5euz33g) gives this example configuration, which might be easier:
```

# main.cf
smtpd_sender_restrictions =
  check_recipient_access =
      regexp:/etc/postfix/hold_outgoing.regexp

```
```

# hold_outgoing.regexp
/example\.com$/  DUNNO  skip my domain
/^/   HOLD  outgoing delivery suspended

```

---

### Post by zer0net on 2012-12-10
> **lisati said:**
> [https://groups.google.com/forum/?fromgroups=#!topic/mailing.postfix.users/kPyh5euz33g](https://groups.google.com/forum/?fromgroups=#!topic/mailing.postfix.users/kPyh5euz33g) gives this example configuration, which might be easier:
```

# main.cf
smtpd_sender_restrictions =
  check_recipient_access =
      regexp:/etc/postfix/hold_outgoing.regexp

```
```

# hold_outgoing.regexp
/example\.com$/  DUNNO  skip my domain
/^/   HOLD  outgoing delivery suspended

```

Thank you for reply,
I had tried that before but it didn't work for me, I guess my problem was that I was using the code but in a hash file instead of regexp file.

seems like its working now, but my second problem is still there... If the email contains both local and non-local email address it gets held in a queue doesn't get delivered to local. How do I fix that.

Thank you

---

