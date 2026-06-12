---
title: "Any GUI for creating a GPG key ?"
date: 2005-11-07
forum: Server Platforms
---

### Post by Biased turkey on 2005-11-07
KDE has a graphical interface for creating a GPG key.
Is there any equivalent package for Ubuntu ( gnome ) ?
tia for any info

---

### Post by jrib on 2005-11-07
Seahorse integrates well with gnome

---

### Post by HJThis on 2005-11-07
Hello,To both of you

May i ask are you using GPG if so can you help me
i just install it & would love to find someone to test it
out with. if one or both of you would like to help me

please say so & how to go about it 

Thank you ;)

---

### Post by Biased turkey on 2005-11-07
[QUOTE=HJThis]Hello,To both of you

May i ask are you using GPG if so can you help me
i just install it & would love to find someone to test it
out with. if one or both of you would like to help me

please say so & how to go about it 

Thank you ;)[/QUOTE]

I have to admit that I never used GPG for sending files to another person.
I only use it for encrypting and decripting my own files, like my passwords list

---

### Post by Biased turkey on 2005-11-07
[QUOTE=_jason]Seahorse integrates well with gnome[/QUOTE]
Thanks, by entering seahorse in the search option of Synaptic I found both Seahorse and gpgp.
I'm gonna try both.
Thanks again

---

### Post by HJThis on 2005-11-07
Hi,Biased turkey

First thanks for the reply hehe that's why i installed it myself
but like the idea of using for E-Mail.

& i also just installed Seahorse well if at one point
you start using for E-Mail please let me know

Thank you :D

---

### Post by jrib on 2005-11-07
There is an extension for thunderbird called "enigmail" that will let you use gpg to send email (it signs them with your key too)

---

### Post by Biased turkey on 2005-11-07
[QUOTE=HJThis]Hi,Biased turkey

First thanks for the reply hehe that's why i installed it myself
but like the idea of using for E-Mail.

& i also just installed Seahorse well if at one point
you start using for E-Mail please let me know

Thank you :D[/QUOTE]

I think I'll stick with seahorse seahorse, at least I was able to create a key and use it to encrypt then decrypt a text file made with gedit.
It should be interesting if we could do some tests via email.
Of course, we'll have to exchange our public key.
Are we allowed to post our email adress on this thread ?

Is there a problem with seahorse? 5 minutes ago I tried to export my key in the menu
remote -> sync and publish key
I selected  a server but the application freeze when I click on the sync button.
I tried with another server but still the same problem.

---

### Post by HJThis on 2005-11-07
Hi,Biased turkey

Yes i think you are right about that i had tried to send one
to a server & same thing happen to me i just gave up after
100 Try's hehe

& just send me the Pub key by PM if you like

Thank you

---

### Post by HJThis on 2005-11-07
Hey,Biased turkey

I have to get going for now but if you like to pass
key's just let me know by PM so we can take it from there

Best of luck

---

### Post by jrib on 2005-11-07
[QUOTE=Biased turkey]
Is there a problem with seahorse? 5 minutes ago I tried to export my key in the menu
remote -> sync and publish key
I selected  a server but the application freeze when I click on the sync button.
I tried with another server but still the same problem.[/QUOTE]

yes that happened to me as well.  I solved it by removing a key server from the list.  I think I just left the mit one  in the list and it worked well.  Doesn't matter since they all sync together anyway I think.

---

### Post by HJThis on 2005-11-07
Hi,_jason

Thanks for the heads-up on this now i can get it working
hey would you like to pass key's  if yes just drop a PM

Thank you

---

### Post by kvidell on 2005-11-07
I can't even get it to generate a key. It just errors out and says "Unable to Generate Key" then puts me back at the final screen.

This happened three times in a row.
Any ideas?
- Kev

---

### Post by XDevHald on 2005-11-07
I am getting the same error on dapper and I am not sure what the deal is...I'll take a look at some recent logs on other users.

---

### Post by HJThis on 2005-11-07
Hey,All

Oh yes same problem here 

hey guy's do you want to pass your key's on if
so PM me up to you

Thank you ;)

---

### Post by Biased turkey on 2005-11-09
[QUOTE=_jason]yes that happened to me as well.  I solved it by removing a key server from the list.  I think I just left the mit one  in the list and it worked well.  Doesn't matter since they all sync together anyway I think.[/QUOTE]

Hi Jason, thanks for the tip, it worked fine.
I was able to send and sync my key to the mit keys server

---

### Post by HJThis on 2005-11-09
Hi,Biased turkey

Can you tell me please if you got my E-Mail????

Best of luck

---

### Post by Seth on 2005-11-09
Guys, please do not sign each other's keys unless you have met in person. This breaks the web of trust.

---

### Post by HJThis on 2005-11-10
Hi,Seth

Hmm This breaks the web of trust

well this would be a problem i myself don't know of anyone
that has gpg so not trusting anyone is hard on my end

Best of luck

---

### Post by Seth on 2005-11-10
[QUOTE=HJThis]Hi,Seth

Hmm This breaks the web of trust

well this would be a problem i myself don't know of anyone
that has gpg so not trusting anyone is hard on my end

Best of luck[/QUOTE]
Then self-signing your key and publishing it on something you control like a website or blog will have to do for now. Or go get a notary public. But GPG isn't a Pok&#233;mon-style "gotta collect signatures" contest. It's a way for people to verify who you are. So if someone who doesn't know who you are signs your key, it adds no credibility, but it does make you look trusted. Bad.

---

### Post by Biased turkey on 2005-11-10
[QUOTE=Seth]Guys, please do not sign each other's keys unless you have met in person. This breaks the web of trust.[/QUOTE]

HJThis and I obviously don't know personally anyone in our respective community who use Ubuntu and want to learn about GPG.
So if you want pay HJThis the roundtrip airline ticket to Montreal, he'll be delighted so we can meet in person :)
Aren't you just too paranoiac ?

---

### Post by HJThis on 2005-11-10
Hi,Seth

Well first let me say i did not repy to you post as
a put down as you can tell i'm new at all this.

had no idea that doing this may/could start a problme
& as for a Blog :confused:  no idea what that is 
it's it something you can download & install????

Best of luck

---

### Post by HJThis on 2005-11-10
Hi,Biased turkey

Yes that's just what i was saying i don't no of anyone
that is using gpg so to go looking for someone.

a lot of the time when i ask someone hey get back
at me. by gpg i get huh

Best of luck

hey what is a Blog

---

### Post by Seth on 2005-11-10
[quote=Biased turkey]HJThis and I obviously don't know personally anyone in our respective community who use Ubuntu and want to learn about GPG.
So if you want pay HJThis the roundtrip airline ticket to Montreal, he'll be delighted so we can meet in person :)
Aren't you just too paranoiac ?[/quote] If I'm too **paranoid**, so is all of Debian. Here's a snippet from the [Debian Keysigning Guide]("http://www.debian.org/events/keysigning"):
> You should never sign a key for somebody else you haven't met personally. Signing a key based on anything other than first-hand knowledge destroys the utility of the Web of Trust. If ones friend presents other developers with your ID card and your fingerprint, but you are not there to verify that the fingerprint belongs to you, what do other developers have to link the fingerprint to the ID? They have only the friend's word, and the other signatures on your key -- this is no better than if they signed your key just because other people have signed it! 
It is nice to get more signatures on ones key, and it is tempting to cut a few corners along the way. But having trustworthy signatures is more important than having many signatures, so it's very important that we keep the keysigning process as pure as we can. Signing someone else's key is an endorsement that you have first-hand evidence of the keyholder's identity. If you sign it when you don't really mean it, the Web of Trust can no longer be trusted.

---

### Post by Biased turkey on 2005-11-10
To Seth: I understand your point of view, but HJThis and  I **don't want to collect keys**.
Why should I trust HJThis less than someone , for example , I met a couple of times at a Linux meeting in Montreal ?
Anyway, to put **my** original post right on the track I found a truckload of GUIs at:
[http://www.gnupg.org/(en)/related_software/frontends.html#nix]("http://www.gnupg.org/(en)/related_software/frontends.html#nix")
GPA looks like the most integrated with Gnome.
I'll install all of them so I can generate a bunch of keys  and **email them** to HJThis  ;)

---

### Post by XDevHald on 2005-11-10
Let's get this back on topic, Seth no one is signing anything, I am not sure why you pulled that out to us.

The main discussion is GPG applications that create keys for the user, also another point out is the Seahorse in which is not working can be directed to the gnome support forum at the top of the forum.

Thanks

---

### Post by majikstreet on 2005-11-10
[QUOTE=Steve Myers]Let's get this back on topic, Seth no one is signing anything, I am not sure why you pulled that out to us.[/QUOTE]
I believe he said that so that they would know not to sign each other's keys unless they met in person.

I am interested in GPG keys, but I have done everything by CLI so far..

EDIT:
I have attached my GPG if anyone wants it.

you can also grab it by doing this in a terminal:
```

gpg --recv-keys BE6B5214

```

-m

EDIT#2: my email for gpg emails: [email]mstreetgpg@gmail.com[/email]

---

### Post by Seth on 2005-11-10
Right. One of them said something about "send me your key so I can sign it" and my comment pertained to the do's and dont's of keysigning.

---

### Post by HJThis on 2005-11-10
Hey,All

Not sure if Seth was talking about me or not if no sorry
but i don't think that anytime i had said anything about
sining any key's what i may have said was pass.

your keys on by PM but as far as i can see if the only
safe way to use gpg is if you met in person then i see
no point in having gpg.

@Biased turkey

send away my friend :D

---

### Post by HJThis on 2005-11-10
Hi,All

Well just incase anyone needs to know i have made a # of key's

1)For Ubuntu friends :)

1)For friends i know

1)For family

1)For the job :(

BOL

Oh again what is a Blog????

---

### Post by HJThis on 2005-11-10
Hey,majikstreet

If it's cool with you may i add you to my Ubuntu gpg list

Best of luck ;)

---

### Post by majikstreet on 2005-11-11
sure! I forgot to mention my email address: [email]mstreetgpg@gmail.com[/email]
I'll edit the original post to add it :P That's an email address I made for GPG only.

---

### Post by ubernoob on 2005-11-17
To explain what Seth means. You can sign your own messages, and encrypt messages to each other without signing each other keys. Just import each other keys in seahorse. It wont make any diffrence if you sign each other keys or not. You can just right click on the key and use "set key trust". Or you can sign the key and choose "do not upload to keyserver".

When you sign someone else key and upload it to a keyserver, you tell everyone else that you trust this guy that he is who he say he is.

I'll try to illustrate this in an example:

Alice and Bob works in the same company. They have alot of customers which deals with alot of money. Alice and Bob takes care of their own customers.  Alice and Bob has signed each other keys, since they can verify them on the office. Alice carefully checks each of her customer before signing their keys, while Bob hasn't learned about this. He sign all the keys without checking. One day Bob signs the key of a person Charlie who has the intentions to rip of some cash from David (one of Alice's customers).

Charlie then makes a huge order from David, and asks him to send the stuff before he sends the money. David sees that Charlie has signed the letter, and get the key from the keyserver. He then sees that Bob has signed Charlies key. Alice works in the same company as Bob, and she has signed Bob's key. David know that Alice checks all the keys carefully. That means David could trust taht Bob really is Bob and work in the same company. Charlie would be trusted implicit, and David sends out the order. You can guess how the story ends.

I hope this examlpe give any sense.

---

### Post by ragman on 2005-11-19
Hi,

Just to let you know. I'm in the U.S. and the Europe Keyserver is the one that stops Seahorse from Syncing. 

BTW I added Ubuntu's Keyserver which is:
keyserver.ubuntu.com 11371

Choose http when you add it. 

The 11371 part goes in the box next to keyserver.ubuntu.com and is the port for those that are not TCP/IP inclined.  :D

---

