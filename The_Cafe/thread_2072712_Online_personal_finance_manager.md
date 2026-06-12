---
title: "Online personal finance manager?"
date: 2012-10-18
forum: The Cafe
---

### Post by Paddy Landau on 2012-10-18
[SIZE=3]**History:**[/SIZE]

I have been using [Quicken]("http://quicken.intuit.com/") for my personal and business finances for many years. A fantastic product, I use an old version (2000) on Wine, but it has become creaky and problematic to use.

If only Quicken supported Linux, I would renew it, but I have not purchased a new version since 2000 because of its problems on Linux.

Despite searching intermittently for a couple of years, I have not found a decent replacement.

[MoneyDance]("http://infinitekind.com/moneydance") is not too bad, albeit a bit clunky. Sadly, I cannot use it for want of two critical tools:

[LIST]
[*]Viewing future predicted balances. There is a "forecaster" plug-in for this, but it is so basic and difficult to manipulate that I cannot use it.
[*]Exporting to CSV has been broken since its inception.
[/LIST]
 
[SIZE=3]**So, I thought…**[/SIZE]

What about using an online finance package, such as [Mint]("https://www.mint.com/") (apparently being purchased by Quicken) or [Buxter]("https://www.buxfer.com/"). ([Quicken's online version]("http://www.intuit.co.uk/quickbooks/accounting-software/online/compare-online-accounting-products.jsp") is crazily expensive.)

Well, the ones that I have looked at are excellent at downloading data directly from your bank — only if your bank allows it, of course, which mine does not.

However…

The ones I've found lack the ability to…

[LIST]
[*]… import transactions you already have from another program (well, one of them does allow this)
[*]… enter your own transactions (if you cannot import from the bank)
[*]… enter future predicted payments and see predictions of future spending and balances
[/LIST]
 
Aargh! ](*,) What's the use of a finance manager if you cannot use it to manage your finances?

[SIZE=3]**My request:**[/SIZE]

I wonder if you can give a recommendation as to which online product, if any, to use?

---

### Post by ajgreeny on 2012-10-18
You don't mention which Linux finance programs you have looked at, but I used Quicken on Windows a long time ago, though I can't remember which version of Quicken it was. Since moving to Ubuntu, and in spite of using gnome or XFCE or LXDE, I have started using KDE's kmymoney2.  I find it very like the Quicken I knew, but that may be related to the old version I used, and your situation may be different.  It does have a forecasting ability, though that is something I do not use personally.

If you did not look at kmymoney2 in your search, do so now; you may find it does all you want. Being a KDE app it will bring in several KDE and qt libs etc etc, but I think it is worth the small space they take.

On a side note I think I would be a bit wary of using an online application for the sort of financial data that I have on my system which I want to keep to myself.

---

### Post by larrys4227 on 2012-10-18
+1 for KMyMoney

---

### Post by oldfred on 2012-10-18
I continued to use XP for many years as I had Quicken data going back to DOS days. I also would buy it if they offered a Linux package but they do not.

I also use kmymoney, and finally shutdown quicken. I was able to import a lot of data but often needed cleanup/changes.

I do not use any forecasting features, so I cannot comment on that.

---

### Post by MoebusNet on 2012-10-18
I've been using gnucash to manage my finances for a number of years now. I do not use all of the capabilities of the program, but it is available through Ubuntu Software Center if you want to read the description.

Details link: [http://www.gnucash.org/features.phtml](http://www.gnucash.org/features.phtml)

---

### Post by MoebusNet on 2012-10-18
Hmmm, it's been long enough now that I don't remember how I got Gnucash. I'm not sure now that it is available through Software Center, however you can download it from:

[http://www.gnucash.org/](http://www.gnucash.org/)

Sorry if I misled anyone.

---

### Post by Paddy Landau on 2012-10-18
Thank you for the answers.

When I last tried GnuCash, I found it a little complicated. I would have persisted, but I need something that my (non-computer-expert) wife and daughter can also use.

Spurred by your comments, I am looking at kMyMoney. I see that there are kMyMoney and kMyMoney2. What is the difference between them?

In the meantime, I have added [Clay Weber's PPA]("https://launchpad.net/~claydoh/+archive/kmymoney2-kde4") and am about to install kMyMoney version 4.6.3. I'll let you know how I get on.

---

### Post by bailout on 2012-10-18
Another one is Skrooge which is also a KDE app.

---

### Post by Paddy Landau on 2012-10-18
> **bailout said:**
> Another one is Skrooge which is also a KDE app.
Thanks, I'll have a look at Skrooge, too.

I am having problems importing my Quicken data into kMyMoney; most transactions come over OK, but some have gone wrong. I shall have to get onto the forums to find out what, as I don't understand the results.

---

### Post by bailout on 2012-10-18
Lots of people seem to have problems with Quicken files. Often caused by the date formet. 

You could try importing into Skrooge to see if that will work. I think Skrooge will import/export kmy files so if you can get your quicken file into skrooge you can then export into kmy.

---

### Post by forrestcupp on 2012-10-18
Quicken Online used to be free at one time. I see now that, like you said, they have bought Mint, and that is their free offering. Hopefully they'll make Mint usable. I used it for a while, and it was good for being able to look at all of your different accounts all at once. But it wasn't good for any manual things at all. Mint wouldn't even allow you to enter your own transactions. You just had to wait for them to post, then they would show up in Mint. In my opinion, that's not any better than just going to the bank's web site. The only benefit it was to me was that it let me look at all of my different banks and credit cards from one app.

Maybe Intuit will take it and make it usable.

> **MoebusNet said:**
> I've been using gnucash to manage my finances for a number of years now. I do not use all of the capabilities of the program, but it is available through Ubuntu Software Center if you want to read the description.

Details link: [http://www.gnucash.org/features.phtml](http://www.gnucash.org/features.phtml)Gnucash is great. It *is* in the repos.

> **Paddy Landau said:**
> Thank you for the answers.

When I last tried GnuCash, I found it a little complicated. I would have persisted, but I need something that my (non-computer-expert) wife and daughter can also use.Gnucash is probably about the best. You're right that it's kind of confusing at first. But it's only setting it up that is complicated at all. After it's set up, it's very easy to use just for inputting your transactions. If you could get it set up, your wife and daughter wouldn't have any trouble using it.

---

### Post by Paddy Landau on 2012-10-19
> **bailout said:**
> Lots of people seem to have problems with Quicken files. Often caused by the date formet.
MoneyDance imports the QIF file perfectly. Unfortunately, Skrooge completely fails to import it.

KMyMoney imports the QIF file, but gives me a message that I don't understand dozens of times: "KMyMoney has matched a downloaded transaction with a manually entered one (result above)". That confuses me, because I am importing into a completely empty file. They appear to be incorrect matches, but even if I "Unmatch" them all, the balances are still incorrect; I have spotted that KMyMoney seems to be duplicating some transactions. I'll get onto the KMyMoney forums to ask for help.

> **bailout said:**
>  You could try importing into Skrooge to see if that will work. I think Skrooge will import/export kmy files so if you can get your quicken file into skrooge you can then export into kmy.
I wonder if I can import into MoneyDance; export from there; and import into KMyMoney or Skrooge?

I'm still working on it (with much frustration) and I'll let you know what happens.

---

### Post by Paddy Landau on 2012-10-19
> **forrestcupp said:**
> Gnucash is probably about the best. You're right that it's kind of confusing at first. But it's only setting it up that is complicated at all. After it's set up, it's very easy to use just for inputting your transactions. If you could get it set up, your wife and daughter wouldn't have any trouble using it.
LOL, you don't know the extent of technophobia with the ladies in this house! They use a computer the way I use a refrigerator — I expect it to just work, and wouldn't have the faintest idea of how to fix a broken one.

But it's heartening to know that GnuCash is easy to use. As I say, I tried once before but became overwhelmed with the setting-up process, especially as I was importing hundreds (perhaps thousands) of transactions and had to make them all work.

I wonder if it would be worth my while paying someone to do the setting-up for me (outsourcing the job)? The problem with that, of course, is that I would not learn the ropes and would have to rely on someone else for anything major.

---

### Post by miraks on 2012-10-22
> **Paddy Landau said:**
> Skrooge completely fails to import it.

Hi,

I am the main developer of Skrooge and I would like to understand the issue you have with Skrooge during import of QIF file.
This is not normal.
Could you tell me what is the error message and eventually send me a sample by email (my email address is in the about of Skrooge, I am Stephane MANKOWSKI).

What is your version of Skrooge?
Do you know you can install the last version from my PPA?
[http://skrooge.org/ubuntu_installation](http://skrooge.org/ubuntu_installation)

Thank you in advance.

---

### Post by Paddy Landau on 2012-10-22
> **miraks said:**
> Do you know you can install the last version from my PPA?
I did, Stephane, thank you, and I do have the latest version of Skrooge.

> **miraks said:**
> Could you tell me what is the error message and eventually send me a sample by email
I shall try to get around to that early this week. Thank you for offering to look at this.

---

### Post by forrestcupp on 2012-10-22
Wow. If you send a sample of your file through email, I'd make sure to remove anything you don't want people to see. Not that Stephane isn't trustworthy, but I would even have a hard time giving my own dad my financial information. (Not that I don't trust him, either. :) )

---

### Post by Paddy Landau on 2012-10-22
> **forrestcupp said:**
> If you send a sample of your file through email, I'd make sure to remove anything you don't want people to see…
Yes, I realise, thanks for the warning. I don't send sensitive information by email. Besides, the files are so large that I'd rather send a smaller sample file.

---

### Post by Penguin360 on 2012-10-22
Have you tried Outright?

---

### Post by Paddy Landau on 2012-10-23
> **CodingBeaver said:**
> Have you tried Outright?
Thanks for the tip. I've just signed up and tried it. Unfortunately, it is like the others — it wants to link directly to your bank, rather than allowing you to import your old transactions (although you can add new transactions). This means that I still cannot use accurate forecasting; I lose all the information that I already have; and I cannot have non-bank accounts (such as, say, cash-in-hand or money-owed).

---

### Post by Lars Noodén on 2012-10-23
> **Paddy Landau said:**
> Yes, I realise, thanks for the warning. I don't send sensitive information by email. Besides, the files are so large that I'd rather send a smaller sample file.

I'd still be careful of what is sent and send only sanitized data, but the risks can be mitigated somewhat by using PGP.  Thunderbird has the plugin Engimail and I expect that there are similar ones for the others.

---

### Post by Paddy Landau on 2012-10-23
> **Lars Noodén said:**
> I'd still be careful of what is sent…
I appreciate what you say, but I don't send out sensitive data via email.

---

### Post by Penguin360 on 2012-10-23
I used MoneyDance 2011 for a while, then I stopped. The main reason is the data validation issue I kept running into. When I choose an expense category, it does not disable the deposit field. And when I choose an income category, it does not disable the payment field. Last time, I accidentally deposited some money into an expense field, and it took me a LONG time to figure out where the money went. (Microsoft Money does a great job on the data validation, but I think they discontinued Microsoft Money.) There is a new version of MoneyDance, MoneyDance 2012, but I don't know if they fixed the issue.

I just tried GnuCash, and it seems to be your best choice at this moment if you don't care about data being stored on your hard drive instead of the cloud. I exported my data from MoneyDance as QIF format and imported into GnuCash, and the import went through smoothly and now I have GnuCash up and running.

---

### Post by forrestcupp on 2012-10-23
> **CodingBeaver said:**
> 
I just tried GnuCash, and it seems to be your best choice at this moment if you don't care about data being stored on your hard drive instead of the cloud.

Well, the obvious solution to that is to store the data file in your Dropbox or Ubuntu One folder. That's what I do. Just _do not_ ever do that with QuickBooks files. QuickBooks saves your changes on the fly, and if you're doing that from Dropbox on two different computers, you can majorly screw things up. I learned that lesson from experience. GnuCash isn't a problem, though, since you manually save your data.

---

### Post by Paddy Landau on 2012-10-23
> **forrestcupp said:**
> … the obvious solution to that is to store the data file in your Dropbox or Ubuntu One folder…
Thanks for the idea, forrestcupp. That is not the problem that I am addressing here; the problem is that I have not managed to find a suitable replacement for Quicken (which is not properly supported in the UK anyway), and I thought that maybe an on-line solution may work.

I am still looking, but I need to follow up on a couple of previous posts first.

---

### Post by forrestcupp on 2012-10-23
> **Paddy Landau said:**
> Thanks for the idea, forrestcupp. That is not the problem that I am addressing here; the problem is that I have not managed to find a suitable replacement for Quicken (which is not properly supported in the UK anyway), and I thought that maybe an on-line solution may work.

I am still looking, but I need to follow up on a couple of previous posts first.

I know. I was just addressing CodingBeaver's problem. ;)

---

### Post by Paddy Landau on 2012-10-23
> **forrestcupp said:**
> I know. I was just addressing CodingBeaver's problem. ;)
OK, cool.

Off-topic: are you really still using 8.04 as your profile states? It's unusual to see someone using such an old version.

---

### Post by forrestcupp on 2012-10-23
> **Paddy Landau said:**
> OK, cool.

Off-topic: are you really still using 8.04 as your profile states? It's unusual to see someone using such an old version.

No. It won't let you go back to old development release profile states after you change them, so I thought I'd hold on to it. I think I used to have Dapper development release, then I learned that lesson the hard way. :)

I'm using 12.10.

---

### Post by Penguin360 on 2012-10-24
> **forrestcupp said:**
> No. It won't let you go back to old development release profile states after you change them, so I thought I'd hold on to it. I think I used to have Dapper development release, then I learned that lesson the hard way. :)

I'm using 12.10.
Oh, I didn't know that. Thanks for the info.

Back on topic: I decided to ditch GnuCash. It is so different from other accounting software. There is no category in GnuCash. Each category is an account, so say if you have an expense on Grocery, then in GnuCash, you will need to create an account Grocery and marked it "Expense" account type. This is very strange to me; unless I am missing something, I am done with GnuCash. Since I have a MoneyDance 2011 license, I can get the free upgrade to 2012. I am going to try the new version of MoneyDance.

---

### Post by Paddy Landau on 2012-10-24
> **CodingBeaver said:**
> There is no category in GnuCash. Each category is an account…
Yes, that is the "correct" way to do double-entry bookkeeping. Like you, I also found it too difficult to work with. Fine for a qualified accountant, no doubt, but not for me.

---

### Post by forrestcupp on 2012-10-24
> **CodingBeaver said:**
> Oh, I didn't know that. Thanks for the info.

Back on topic: I decided to ditch GnuCash. It is so different from other accounting software. There is no category in GnuCash. Each category is an account, so say if you have an expense on Grocery, then in GnuCash, you will need to create an account Grocery and marked it "Expense" account type. This is very strange to me; unless I am missing something, I am done with GnuCash. Since I have a MoneyDance 2011 license, I can get the free upgrade to 2012. I am going to try the new version of MoneyDance.

Once you have it all set up, you'll have an account set up for your whole checking account. Then you can click on that to go to the ledger for your checking account. Once you're in there, all of those accounts pretty much act exactly like categories in other software. I only use GnuCash for my checking ledger. Once you have that ledger open, it will automatically open to that ledger every time you open GnuCash. Then you can just think of all of those accounts as categories, and it will be very familiar to you.

If you import from a qif file or something, you don't even have to think about it. Just find your bank's checking account in the accounts list and double click on it to go straight to your ledger. Then you can pretty much just start using it. I don't remember if I had to set an initial balance to cause it to reconcile, or not.

---

### Post by Penguin360 on 2012-10-24
> **forrestcupp said:**
> Once you have it all set up, you'll have an account set up for your whole checking account. Then you can click on that to go to the ledger for your checking account. Once you're in there, all of those accounts pretty much act exactly like categories in other software. I only use GnuCash for my checking ledger. Once you have that ledger open, it will automatically open to that ledger every time you open GnuCash. Then you can just think of all of those accounts as categories, and it will be very familiar to you.


I see. I will give GnuCash another try. 

I hate Unity...if you use GnuCash with normal window size, you will easily miss the menu bar, because it is at the top of the desktop!!!! And you will find your GnuCahs window like as shown in the attached screen shot.:mad:

I was staring at the GnuCash window for a while trying to see how I can open a file, or save a file I am working on. It took me a while to realize that I have to hover my mouse all the way to the top of the desktop to get to the menu bar!!!!!

---

### Post by Paddy Landau on 2012-10-25
> **CodingBeaver said:**
> It took me a while to realize that I have to hover my mouse all the way to the top of the desktop to get to the menu bar!
But that is standard Unity. All programs (with the exception of Libre Office (until 12.10) and root GUIs) do this.

---

### Post by Penguin360 on 2012-10-25
> **Paddy Landau said:**
> But that is standard Unity. All programs (with the exception of Libre Office (until 12.10) and root GUIs) do this.
Yeah, I am still not used to it. 

But now I am getting used to GnuCash. Like forrestcupp said, once you have it set up, it works very well. I save my GnuCash book in the cloud so I can access it from different computers.

---

### Post by MasterNetra on 2012-10-29
Found this via alternativeto.net: [http://frontaccounting.com/wb3/](http://frontaccounting.com/wb3/)

---

### Post by Androzani1 on 2012-10-29
What does MA think? :P

---

### Post by Paddy Landau on 2012-10-30
> **MasterNetra said:**
> Found this via alternativeto.net: [http://frontaccounting.com/wb3/](http://frontaccounting.com/wb3/)
Thank you. It's not ready for release yet, but I'll keep an eye on it.

> **Androzani1 said:**
> What does MA think?
Who is MA?

---

