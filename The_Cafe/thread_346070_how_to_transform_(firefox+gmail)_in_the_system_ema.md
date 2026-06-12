---
title: "how to transform (firefox+gmail) in the system email client"
date: 2007-01-25
forum: The Cafe
---

### Post by andrea.tagliasacchi on 2007-01-25
Hi there, 

i am not rally an amateur of POP3 mail clients, that's why i switched completely to gmail by now.

     In order to get notification of new posts i use kcheckgmail ( which sometimes doesn't really work well, like right now, where after i read a new post the new message notification remains active ).

     The google toolbar instead gives me the ability to click on a mailto address in order to simply open a new tab/window with the compose message and the TO: field already filled.

     What i would really like to do know is to set firefox+gmail as the only mail client in the system.
That is when i click on "send to..." in konqueror or in other programs i would like to have a new gmail compose window to open with the fields already filled.

     Since google toolbar give similar functionalities but limited to the firefox scope i tried to explore the firefox settings (particularly about:config). As you can see (if you have googletoolbar installed) there are several voices active if you filter results with the key "gmail" but the following is the only interesting one:

>  name:google.toolbar.mailto.providers.Gmail
value:firetool-mail:[http://mail.google.com/mail/?view=cm&fs=1@to=to&subject=su&body=body&cc=cc&bcc=bcc&name=Gmail](http://mail.google.com/mail/?view=cm&fs=1@to=to&subject=su&body=body&cc=cc&bcc=bcc&name=Gmail)
Looking at this entry i am able to run a command like (from terminal for example):

>  firefox "http://mail.google.com/mail/?view=cm&to=email@gmail.com&subject=this is the subject&body=This is the body&cc=ccemail@gmail.com&bcc=bccemail@gmail.com&name=Gmail&fs=1"
as you can easily try it works quite fine... however there are some problems with some fields:[LIST]
[*] view= what this field is?[/LIST][LIST]
[*] subject= doesn't seem to work whatever you write it doesn't appear in the email subject[/LIST][LIST]
[*] name= Gmail, what does this field do?[/LIST][LIST]
[*] fs=1, what does this field do?[/LIST]And the most important question, do you know if any attachment=XXXX field exists?
that would allow to just put the attachment path in the query and complete the functionalities.

To conclude the setup of the prefferred mail client system settings, that is:
 
>             kcontrol->kde components->default applications->email client 
Where we can choose another program to be run instead of kmail. I would put the previous firefox command but the fields have to be initialized with the contextual one. 
In some similar occasion i have seen that a % followed by a letter is used (like %a %t ecc.. ), which are in this particular case the symbols to be used to fill the to, subject, cc, bcc, ecc..?


Thanks for the answers, 
Hope this would be helpful for other people
Andrea

---

### Post by Aetherius on 2007-01-25
dunno about the rest but the 'view' field is where you are at within gmail 'view=cm' means you are **c**o**m**posing an email. try it with other abbreviations and see what happens 'in' or 'ot' or something


EDIT: 'sm' seems to give you a blank page, while almost everything else gives you a server error....odd

---

### Post by andrea.tagliasacchi on 2007-01-25
> **Aetherius said:**
> dunno about the rest but the 'view' field is where you are at within gmail 'view=cm' means you are **c**o**m**posing an email. try it with other abbreviations and see what happens 'in' or 'ot' or something


EDIT: 'sm' seems to give you a blank page, while almost everything else gives you a server error....odd
well with:

> [http://mail.google.com/mail/?view=ot](http://mail.google.com/mail/?view=ot)
[http://mail.google.com/mail/?view=in](http://mail.google.com/mail/?view=in)

i just get:

> **Server Error**
        [SIZE=-1] We're sorry, but Gmail is temporarily unavailable. We're currently working to fix the  			problem -- please try logging in to your account in a few minutes.[/SIZE]
               

maybe later will work...

---

### Post by Aetherius on 2007-01-25
yeah i get the same, they were just suggestions :oops:  theres bound to be similar codes for inbox/outbox/spam etc

---

### Post by lm8 on 2011-09-07
> **andrea.tagliasacchi said:**
> 
Looking at this entry i am able to run a command like (from terminal for example):
 
 

as you can easily try it works quite fine... however there are some problems with some fields:
[LIST]
[*]view= what this field is?
[/LIST]
[LIST]
[*]subject= doesn't seem to work whatever you write it doesn't appear in the email subject
[/LIST]
[LIST]
[*]name= Gmail, what does this field do?
[/LIST]
[LIST]
[*]fs=1, what does this field do?
[/LIST]And the most important question, do you know if any attachment=XXXX field exists?
that would allow to just put the attachment path in the query and complete the functionalities.
 
To conclude the setup of the prefferred mail client system settings, that is:
 
Where we can choose another program to be run instead of kmail. I would put the previous firefox command but the fields have to be initialized with the contextual one. 
In some similar occasion i have seen that a % followed by a letter is used (like %a %t ecc.. ), which are in this particular case the symbols to be used to fill the to, subject, cc, bcc, ecc..?

 
From what I've been able to find, view=cm sets the view to compose mode. The fs field sets the browser window to fullscreen. There's also a tf for tearoff which displays the information without the surrounding menus and search area. Instead of subject=, use su=. There are also settings for to, body, cc and bcc.
 
All references I could find indicate there's no current way to attach a file via a URL. It's considered a security risk. There appear to be ways to do this using other APIs to access Google Mail.
 
I haven't tried setting Google Mail as my default on Linux yet, but from what I've read one can uses the update-alternatives command to change the /etc/alternatives/mta symlink and other related symlinks.
 
I have a mailto: script that works with v8cgi, parses a mailto: command and calls whatever browser is specified in the script passing a URL that will open the Google Mail Compose Mail window. You can find it here along with any other useful Google Mail tips and tricks I've been able to dig up so far:
[http://www.distasis.com/cpp/gmail.htm](http://www.distasis.com/cpp/gmail.htm)

---

