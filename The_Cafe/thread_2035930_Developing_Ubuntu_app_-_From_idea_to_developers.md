---
title: "Developing Ubuntu app - From idea to developers"
date: 2012-07-31
forum: The Cafe
---

### Post by Redi46464 on 2012-07-31
Hi,
first of all I really do not know if this is the right place on UbuntuForums.org to post this, but since I can't pick up different place I will just post it here, it's just an idea anyway. :)

I'm Ubuntu user since 8.04 LTS and even after trying out dozens of other distros like Fedora, Chakra, Debian, Arch, LMDE etc. I always returned back to my beloved OS. During the 11.04 release I was introduced to the new Unity DE and I fell in love.
It was just the best DE I found and since then I thought about converting all the WinXP machines in our company to Ubuntu.

I finally succeed and with the 11.10 release we were up and running (except one WinXP machine that was needed for some special Brother printer, but that is now settled, we just bought compatible printer :)). We previously used Thunderbird and Firefox for web/mail related tasks and some old (97?) M$ Word, so the transition to OO (and later to LO) was pretty smooth. We even bought new HW with Ubuntu and ecology in mind (Now it's just one AMD C-60 machine, but we want to continue with these savings in the future).

The biggest problem in this "trip to OSS" was accounting app. Previously we used old [DOS app]("http://www.jezeksw.cz/gfx/homepageStereo.png") and our needs were pretty simple, we just needed some sort of DB with information about all our costumers, DB with invoices and an easy way to create one, DB with all the items we had in our store and few other things.
First I tried to find open-source alternative. I found [GNUCash]("http://www.gnucash.org/") but it turned out that their implementation of "Small-Business accounting" is pretty much useless. Then I found KDE app [Kraft]("http://www.volle-kraft-voraus.de/"), but their UI was just one of the worst I've ever seen and worked with. I've found few more apps, but all of them lacked elementary features. That forced us to use commercial Java-(very slow)-based-cloud-hosted app [Flexibee]("http://www.flexibee.eu/"), I also started to think about extremely fast, GTK3 based accounting app.
I came up with basic UI mockup and functions that I as a "small-business" user with few employees and approximately 2 000 invoices per year would need. Some of these features were:

[LIST=1]
[*]Speed. This is what I call "the ultimate goal". After I talked with people using all kind of accounting SW I found out that slow response is their main problem. These people want to work, not wait for the window to scroll down. I also think that for simple office use Tegra3 or C-60 computer should be enough.
[*]Clean and simple GUI.
[*]Ability to quickly and easily create invoices. The main thing that people do in these apps are (surprisingly :)) invoices. I would like to do this simply and effectively with some extra eye-candy (different layouts for invoices, nice and simple print outputs etc.).
[*]Database of contacts with things like company logos, address etc. Maybe later connected with Thunderbird contact list to make communication easier.
[*]Storage database. Prices of every single item, VAT, stock availability etc.
[*]Fulltext search.
[*]Modularity. The user should have full control over every setting, composition of docks etc.
[*]Complete Ubuntu integration. Later maybe even with our own lens etc.
[*]Write the whole app in Vala? With the first release using basic MySql database?
[*]Don't worry I have even more ideas :)
[/LIST]
I would like to make this one right. I think that the Linux world have enough half-done video players, music players, text editors, web browsers etc. We need stable base for users and accounting app is one of the must-have. Most of the "small-business" people need good web browser (we already have that), good email client (we already have that), good office suite (we already have that) and good accounting app.

So after I told you all the things I have I can tell you what I don't have and what can I offer. :-k

 I'm not a programmer so I can't make the app by myself. I also never worked in this industry, so I do not have any software developing related experience. But I can offer you my ideas with all the long experience of using these apps, paid web hosting and maybe even some kind of advertising.
And at the very end. The main question. Why am I writing this :).

Do you think that there is a place in the OSS community for a member with nothing more than an idea, small amount of money and insight into the problem, who want to help create a great app that will push the Linux and Ubuntu OS further?


Also I know that there is openERP, but that is just overkill. We need smaller app for the majority of user with businesses.

*Also, please excuse my poor English and feel free to fix my mistakes. I'm not a native speaker but I would like to learn more.*

---

### Post by Cheesehead on 2012-07-31
What you are discussing is bookkeeping more than accounting. Accounting is the ability to summarize income, expenses, and equity by various criteria. Good accounting starts with good bookkeeping, but also includes payroll, taxes, inventory, audits, and the management reports you need to make intelligent business decisions.

There are already several quite good accounting applications in Linux. All are paid. Few, if any, are in Software Center, but that's okay.

You see, the personal relationship between the business owner or manager and the accountant (the one who signs tax forms as the preparer) is more important for my business, and those of my peers, than the actual software choice.

There's a trust relationship - I need to be able to trust my accountant to keep me out of trouble with the tax authorities and the labor board. Payroll deductions must be correct, periodic filings must be made and accurate, payments must be made on time, inventory adjustments must be properly documented.

Bookkeeping costs are pretty much fixed, regardless of the bookkeeping package I use, since most of the current bookkeeping packages -regardless of OS- have the same features (single entry, customer database, custom invoices, easy searchability, etc) and work pretty much the same. However, accountant billable hours is a variable cost, and the variation depends very much on which package you use. Using the one the accountant prefers to work with has a *big* difference in the number of billed hours. The average cost of most good accounting packages for small business is generally a fraction of the accountant's yearly fees, so the cost of any particular package is not an important criteria.

---

### Post by juancarlospaco on 2012-07-31
> **Redi46464 said:**
> 
[LIST=1]
[*]Speed. 
[*]Clean and simple GUI.
[*]Ability to quickly and easily create invoices. 
[*]Database of contacts. Maybe later connected with Thunderbird.
[*]Storage database. 
[*]Fulltext search.
[*]Modularity. 
[*]Complete Ubuntu integration. 
[/LIST]


You are Describing Base:

[http://www.libreoffice.org/features/base/](http://www.libreoffice.org/features/base/)

Maybe you get better luck by hiring a per-objective LibreOffice expert...

---

### Post by Redi46464 on 2012-08-01
> **Cheesehead said:**
> What you are discussing is bookkeeping more than accounting. Accounting is the ability to summarize income, expenses, and equity by various criteria. Good accounting starts with good bookkeeping, but also includes payroll, taxes, inventory, audits, and the management reports you need to make intelligent business decisions.
I tried to Google and DuckDuckGo with "book keeping Linux" and I found the same apps as before. Can you please point me at some useful app?

> **Cheesehead said:**
> There are already several quite good accounting applications in Linux. All are paid. Few, if any, are in Software Center, but that's okay.
We actually use one of those apps, my problem is that I'm not satisfied with it and with the current state of Linux book keeping :)

> **Cheesehead said:**
> You see, the personal relationship between the business owner or manager and the accountant (the one who signs tax forms as the preparer) is more important for my business, and those of my peers, than the actual software choice.

There's a trust relationship - I need to be able to trust my accountant to keep me out of trouble with the tax authorities and the labour board. Payroll deductions must be correct, periodic filings must be made and accurate, payments must be made on time, inventory adjustments must be properly documented.

Bookkeeping costs are pretty much fixed, regardless of the bookkeeping package I use, since most of the current bookkeeping packages -regardless of OS- have the same features (single entry, customer database, custom invoices, easy searchability, etc) and work pretty much the same. However, accountant billable hours is a variable cost, and the variation depends very much on which package you use. Using the one the accountant prefers to work with has a *big* difference in the number of billed hours. The average cost of most good accounting packages for small business is generally a fraction of the accountant's yearly fees, so the cost of any particular package is not an important criteria.
Don't know how it works in state of Wisconsin but here in central Europe almost every accountant have their special piece of SW that is in 90% different than the app the businessman use. Everything is then made over some .xml/.xls exports. So the used software on the client side is irrelevant. Of course that we could just use the same SW as the accountant and connect it trough some cloud storage, but most people here don't do it (These apps have their own market and they are more expensive than the usual ones. Only big companies use this kind of system.). There is just so many small businesses that they will never use the same app. I know that it's all about relationship between you and your accountant so you will be sure that no laws were broken. But the attitude of "they use this and they will always use this" is simply wrong.
And my goal is not to cut cost, if you use Linux because you don’t need to pay for it, the we have different goals. I use it because it's simply superior to M$ and Apple (and yes I own/owned both) and I just want make it better.

> **juancarlospaco said:**
> You are Describing Base:

[http://www.libreoffice.org/features/base/](http://www.libreoffice.org/features/base/)

Maybe you get better luck by hiring a per-objective LibreOffice expert...
I'm not sure if LO have the best interface for this kind of work or if the underlying engine is fast enough. Or are there any similar projects which I can try?

---

