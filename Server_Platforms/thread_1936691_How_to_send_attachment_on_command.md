---
title: "How to send attachment on command"
date: 2012-03-06
forum: Server Platforms
---

### Post by satimis on 2012-03-06
Hi all,

I'm following;
Postfix Virtual MailBox Clam Smtp Howto
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#Set_up_Postfix_to_use_virtual_mailboxes](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#Set_up_Postfix_to_use_virtual_mailboxes)

building a mail server.

Coming to;
Test ClamSMTP for outgoing mail
Send this file as an attachment to [email]info@domain1.com[/email]
(it is a virus .zip file)

$ uuencode eicar_com.zip | mail [email]info@domain1.com[/email]
It was hanging there for prolonged time.  I have to cancel it manually.

$ mutt -s "Test mail" -a eicar_com.zip [email]info@domain1.com[/email] < /tmp/mailmessage.txt ```

Can't stat info@domain1.com: No such file or directory
info@domain1.com: unable to attach file.

```

Any clue?  TIA

B.R.
satimis

---

### Post by Jonathan L on 2012-03-06
Hi Satamis

1. **_ Uuencode_**

I don't think you need uuencode for the attachment in mutt.  Nonetheless here's what's going on: The arguments to uuencode are confusing: with a single argument it's the name (that you want uuencode to use in its output) not the file to open.  This is (probably) what you meant:

```
$ uuencode /etc/magic name-for-transmission
begin 644 name-for-transmission
M(R!-86=I8R!L;V-A;"!D871A(&9O<B!F:6QE*#$I(&-O;6UA;F0N"B,@26YS
M97)T(&AE<F4@>6]U<B!L;V-A;"!M86=I8R!D871A+B!&;W)M870@:7,@9&5S
58W)I8F5D(&EN(&UA9VEC*#4I+@H*
`
end

```If you don't give two arguments, uuencode is reading stdin and waiting for you to type.

The name in the uuencode output is the default filename which the receiving system will use, if not over-ridden by the receiving user.  Normally you'd use just the basename of the file, in your case that would be 'eicar_com.zip'.  (But to repeat, I don't think you need uuencode if you're using mutt.)

2.  **_mutt options_**

The options to mutt are also a little confusing.  Per the man page:


 ```
   -a file [...]
              Attach a file to your message using MIME.  When attaching single
              or multiple files, separating filenames and recipient  addresses
              with  "--" is mandatory, e.g. [COLOR=Red]mutt -a image.jpg -- addr1[/COLOR] or mutt
              -a img.jpg *.png -- addr1 addr2.  The -a option must  be  placed
              at the end of command line options.
```So you need to do something like:
```
mutt -s "Test mail" -a eicar_com.zip[COLOR=Red] --[/COLOR] [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL] < /tmp/mailmessage.txt
```Note the double-dash after eicar_com.zip

And of course, as in the instructions: use your own domain names instead of the domain1.com example.


Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by satimis on 2012-03-06
> **Jonathan L said:**
> Hi Satamis

1. **_ Uuencode_**

I don't think you need uuencode for the attachment in mutt.  Nonetheless here's what's going on: The arguments to uuencode are confusing: with a single argument it's the name (that you want uuencode to use in its output) not the file to open.  This is (probably) what you meant:

```
$ uuencode /etc/magic name-for-transmission
begin 644 name-for-transmission
M(R!-86=I8R!L;V-A;"!D871A(&9O<B!F:6QE*#$I(&-O;6UA;F0N"B,@26YS
M97)T(&AE<F4@>6]U<B!L;V-A;"!M86=I8R!D871A+B!&;W)M870@:7,@9&5S
58W)I8F5D(&EN(&UA9VEC*#4I+@H*
`
end

```If you don't give two arguments, uuencode is reading stdin and waiting for you to type.

The name in the uuencode output is the default filename which the receiving system will use, if not over-ridden by the receiving user.  Normally you'd use just the basename of the file, in your case that would be 'eicar_com.zip'.  (But to repeat, I don't think you need uuencode if you're using mutt.)

2.  **_mutt options_**

The options to mutt are also a little confusing.  Per the man page:


 ```
   -a file [...]
              Attach a file to your message using MIME.  When attaching single
              or multiple files, separating filenames and recipient  addresses
              with  "--" is mandatory, e.g. [COLOR=Red]mutt -a image.jpg -- addr1[/COLOR] or mutt
              -a img.jpg *.png -- addr1 addr2.  The -a option must  be  placed
              at the end of command line options.
```So you need to do something like:
```
mutt -s "Test mail" -a eicar_com.zip[COLOR=Red] --[/COLOR] [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL] < /tmp/mailmessage.txt
```Note the double-dash after eicar_com.zip

And of course, as in the instructions: use your own domain names instead of the domain1.com example.


Hope that's of some use.

Kind regards,
Jonathan.

Hi Jonathan,

Your advice works for me.  Thanks

satimis

---

