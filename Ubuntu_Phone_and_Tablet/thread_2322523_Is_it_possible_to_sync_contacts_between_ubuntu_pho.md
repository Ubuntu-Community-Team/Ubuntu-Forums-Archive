---
title: "Is it possible to sync contacts between ubuntu phone and my desktop?"
date: 2016-04-28
forum: Ubuntu Phone and Tablet
---

### Post by naomibrown on 2016-04-28
I've currently got a Ubuntu phone and Ubuntu running on my laptop. I'm thinking about what the best way to share my contacts between my phone and laptop is. Currently I've got a lot of email addresses and some phone numbers saved in my google contacts list. Are there any other options other than doing this? I've also got a paper based address book which I would like to add information from. 

Any ideas?

Thanks,
Naomi

---

### Post by nothingspecial on 2016-04-28
Hi

You can either sync your google contacts or use syncevolution - [https://help.ubuntu.com/community/SyncEvolution](https://help.ubuntu.com/community/SyncEvolution)

I think it is easier to use google contacts. Add your google account to your Ubuntu Phone, then go to the contacts app and press the circular arrow in the top right corner. After a few minutes your google contacts should be there.

---

### Post by Holger_Ludwig on 2016-04-29
Export your contacts in an vcf-file. Send it to yourself via email. Use Dekko on your Ubuntu Phone to import the file out of the email into your contacts.

Stupid workflow, but unfortunately, after 1 year the Ubuntu Phone is on the market, there is still a lack of some essential functions... !!!!!! like syncing calendar/contacts with e.g. Owncloud
Using google contacts doesn't seem to be a real alternative because using Ubuntu is the reason of numerous users to AVOID sniffing systems like google / Android / Windows ....

---

### Post by naomibrown on 2016-05-02
I'd prefer not to use google contacts to keep all of my contacts, but I don't think I understand what to do for the other method.  

> **Holger_Ludwig said:**
> Export your contacts in an vcf-file. 

I've just looked at google contacts on my laptop and it appears to only have the options to export as: google CSV, outlook CSV and vCard. Which of these should I choose? 

> **Holger_Ludwig said:**
>  Use Dekko on your Ubuntu Phone to import the file out of the email into your contacts. 

I haven't set this up with an email account yet. Do I need to do this first? 

Thanks!
Naomi

---

### Post by Holger_Ludwig on 2016-05-02
> **naomibrown said:**
> I've just looked at google contacts on my laptop and it appears to only have the options to export as: google CSV, outlook CSV and vCard. Which of these should I choose? 
vCard should be perfect 

> **naomibrown said:**
> 
I haven't set this up with an email account yet. Do I need to do this first? 

Yes, first you should set up Dekko with your standard email account you usually use on your laptop
then your're ready to receive your email(s) and the one with the appended vCard Export file

---

### Post by ales-horak on 2016-05-03
> **Holger_Ludwig said:**
> 
[QUOTE=naomibrown;13482109]I haven't set this up with an email account yet. Do I need to do this first?
Yes, first you should set up Dekko with your standard email account you usually use on your laptop
then your're ready to receive your email(s) and the one with the appended vCard Export file[/QUOTE]

why don't you just use scp from the phone? It is very easy and you do not need to enter the phone's terminal app any more. See e.g. [https://gurucubano.gitbooks.io/bq-aquaris-e-4-5-ubuntu-phone/content/en/chapter1.html](https://gurucubano.gitbooks.io/bq-aquaris-e-4-5-ubuntu-phone/content/en/chapter1.html)

---

