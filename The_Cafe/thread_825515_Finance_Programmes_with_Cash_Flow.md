---
title: "Finance Programmes with Cash Flow"
date: 2008-06-11
forum: The Cafe
---

### Post by Purplemunchkin on 2008-06-11
Hi all

Apologies if this is in the wrong place or has been answered before, but as you can see from my post count I'm a newbie here and all these various forums are a bit daunting to start with.

I've just started using Ubuntu and am keen to move as much as I can away from Windows but I'm having trouble finding a personal finance programme that offers daily cash flow projections combining income and expenditure.

Maybe I'm just not looking hard enough in the programmes I've tried:
* Eqonomize won't combine income and expenditure
* MyMoneyEx only takes snapshots of one day a month (I don't know about you, but my finances can fluctuate quite a bit in that time.)
* And I just can't seem to find a cash flow projection report at all in GnuCash, KMyMoney, Grisbi, HomeBank or MoneyDance

Any suggestions to help me replace MS Money would be greatly received!

Thanks

Purp

---

### Post by dasunst3r on 2008-06-11
The last time I used GnuCash (about a year ago), I was able to do a cash flow analysis.  It is under "Reports" in the program's menu bar.  You can do it for an arbitrary timespan, and it breaks stuff down into categories, and will allow you to see specifically what transactions went into the report.

---

### Post by Hei Ku on 2008-08-25
You can try KMyMoney 0.9. There is forecast and budget in the new version.

---

### Post by ffejwilson on 2008-08-29
I just downloaded kmymoney from synaptic package mgr - the version is 0.8.8.  Looked briefly, but don't see the forecast.  Not sure if I'm using the right term or not - but by forecast, I'm looking for something that will take my current balance and project balances (by day) based on future scheduled transactions.  (I'm new and green to ubuntu - working with gnucash at the moment, but can't find that kind of forecast in it either - the cash flow report is historical only, from what I can tell.)

I don't know how to install other than using the package manager - not up on compiling or using terminal commands yet.....

Ideas?

---

### Post by Hei Ku on 2008-09-22
Forecast is available in the 0.9 version and above.
You can install from a PPA package here:

[https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

---

### Post by ffejwilson on 2008-10-12
Hi Hei Ku,

I don't even know what to do once I get to Clay's Launchpad site.  Can you provide step-by-step instructions?  Or am I just too green to move forward with trying to get pre-released material?

Appreciate your help,
Jeff

---

### Post by Hei Ku on 2008-10-14
In either Adept or Synaptic go to the Manage repositories option.

Add this repository:

if you are using Hardy:

deb [http://ppa.launchpad.net/claydoh/ubuntu](http://ppa.launchpad.net/claydoh/ubuntu) hardy main

if you are using Intrepid:

deb [http://ppa.launchpad.net/claydoh/ubuntu](http://ppa.launchpad.net/claydoh/ubuntu) intrepid main

After that, you should have the option to install KMyMoney directly from the repositories, just like you installed 0.8.8 version.

BTW, we are working on a detailed guide, but it is not finished yet.

---

### Post by ffejwilson on 2008-10-28
Thanks Hei!  I got 0.9.2 installed via Synaptic, no problem.

Looking it over, however, the Forecast appears to be statistical based rather than based on actual expenses coming up in the Schedule.  I haven't spent a lot of time with it yet, but if that's true, that's not what I'm looking for.  The one feature of Microsoft Money I love is to view (graphically) a balance of my checking account based on future deposits and withdrawals from the upcoming scheduled transactions.  Does KMyMoney do that (doesn't have to be graphical)?

Thanks,
Jeff

---

