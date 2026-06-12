---
title: "Help: Linux Point-Of-Sale (POS) software ???"
date: 2006-04-16
forum: The Cafe
---

### Post by mips on 2006-04-16
Hi,

Looking to setup a POS system in a restaurant. Need about 2 POS systems with cash registers connecting to a backend server that does all the transaction processing & stock control.

I have found [http://l-ane.net/](http://l-ane.net/) which looks good but this environment is foreign to me.

Systems must utilise touch screen technology. So harware tips would also be great.

I would like some advice from people who have done this before. What hardware/software etc do I need ?

This is for a restaurant/lounge that sells food & drink + I would like a integrated stock control system.

EDIT: Also needs to print receipts and possibly integrate with credit/debit card facilities.

---

### Post by dermotti on 2006-04-16
Well....

[http://squirrelsystems.com/](http://squirrelsystems.com/)

Uses Linux dumb terminals that boot off bootp. The backend server is windowsXP with SQL server though....

---

### Post by mips on 2006-04-16
[QUOTE=dermotti]Well....

[http://squirrelsystems.com/](http://squirrelsystems.com/)

Uses Linux dumb terminals that boot off bootp. The backend server is windowsXP with SQL server though....[/QUOTE]

Thanks. I need to stay away from software/OS of a closed nature.

---

### Post by bonzodog on 2006-04-16
Well, a search has turned up a few: 
Ubuntu has one in it's repos: Tkkasse which is a POS client server system designed specifically for restaurants. Not sure if it is touch screen though.

Also, a commercial Linux solution: [http://www.viewtouch.com/](http://www.viewtouch.com/)

Then look here:[http://sourceforge.net/search/?forum_id=0&group_id=0&atid=0&words=POS+software&type_of_search=soft](http://sourceforge.net/search/?forum_id=0&group_id=0&atid=0&words=POS+software&type_of_search=soft)

Hope this helps :)

---

### Post by mips on 2006-04-16
Thanks, will have a look at those.

From the above links Tina POS looks good. Activity is good. Also looks very similair to a locally sold product...

I need advice from someone in the field that knows what is good and what is not. Also hard to tell how active a project is and how good big/good the support base is. I'm not familair with this environment so need all the help i can get.

Thx again.

---

### Post by dermotti on 2006-04-17
Are you going to be processing gift cards or credit cards? You will need a driver, probly supplied by the CC/giftcard processor. Hopefully they have a driver that will work for these systems....

---

### Post by mips on 2006-04-17
[QUOTE=dermotti]Are you going to be processing gift cards or credit cards? You will need a driver, probly supplied by the CC/giftcard processor. Hopefully they have a driver that will work for these systems....[/QUOTE]

Will do credit cards. I suppose a normal cc machine will be fine and then just capture the payment on the system as CC with the number of the card.

Unless there is a easy way of doing tis via linux. L'ane & Europos have a TCLink pluging for cc, [http://l-ane.net/use/plugins.html](http://l-ane.net/use/plugins.html)

---

