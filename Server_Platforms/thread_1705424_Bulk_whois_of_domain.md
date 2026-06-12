---
title: "Bulk whois of domain"
date: 2011-03-12
forum: Server Platforms
---

### Post by ubbrown88 on 2011-03-12
For the last 5 days, I am getting spam at a very fast rate from different domains, I want to do a bulk whois on all of them and save the result in a text file. 

i created a file domains.txt having domain names

and then I ran the command whois domains.txt
and domains.txt whois

Both shown me errors. I am new to linux, so please help me.

What i want is that it will do a whois of the domains contained in the file domains.txt and save the results in another net text file of all the whois info of all domains.

Thanks

---

### Post by SeijiSensei on 2011-03-12
Just curious, but why?  Do you think that you can somehow contact the domain owners and report the spamming?  Most spams use forged From headers and are sent by networks of hijacked Windows computers.  I get spams allegedly from "aol.com."  AOL has no control over someone forging its domain in a From address.  "Fighting" spam by contacting domain owners is a useless endeavor.  You're much better off running good filtering software like SpamAssassin or using a mail client that supports spam filtering like Thunderbird.

---

### Post by ubbrown88 on 2011-03-12
yes thats what I am thinking.

also, I am just curious if doing bulk whois is not possible or not, it just looks too much exciting, I meant for years I was using windows, and now when I shift to ubuntu, I think I have a very powerful toy siting in right front of me who can do almost anything I want.

---

### Post by koenn on 2011-03-12
> **ubbrown88 said:**
>  I think I have a very powerful toy siting in right front of me who can do almost anything I want.
it's powerful in the way an electrician's toolbox is powerful :
- you need to know the tools, what they're for, how to use them
- you need to know about electricity and understand electrical installations in order to know what to do, and what tools you can use to do it.

here's 1 way of doing whois on your list of domains:
```

while read X; do whois $X;done <domains.txt |more

```




the smart thing to do is to use spam filtering, of course.

---

### Post by Vegan on 2011-03-12
i like spamassassin

---

### Post by ubbrown88 on 2011-03-12
> **koenn said:**
> it's powerful in the way an electrician's toolbox is powerful :
- you need to know the tools, what they're for, how to use them
- you need to know about electricity and understand electrical installations in order to know what to do, and what tools you can use to do it.

here's 1 way of doing whois on your list of domains:
```

while read X; do whois $X;done <domains.txt |more

```


the smart thing to do is to use spam filtering, of course.

Thank you very much.

---

