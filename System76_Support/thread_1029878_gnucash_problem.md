---
title: "gnucash problem"
date: 2009-01-03
forum: System76 Support
---

### Post by eyecreate on 2009-01-03
I've been trying to use gnucash to do my banking, but can not get it to do the crucial thing I've been needing, online banking support. I have the version in intrepid that comes with online banking support, but whenever I try to hook up my account at 53.com, aqbanking crashes. When I tried to run the wizard by command line, it spits this out:

```
3:2009/01/03 21-02-36:gwen(13501):io_tls.c: 1154: gnutls_handshake: -9 (A TLS packet with unexpected length was received.) [fatal]
3:2009/01/03 21-02-36:(null)(13501):provider.c:  659: Error exchanging getAccounts-request (-66)
3:2009/01/03 21-02-36:qt3_wizard(13501):cfgtabpageuserofx.cpp:  283: Error requesting account list

```

I was able to get my account to sync using moneydance, so I know it can work, but I'd love to have the opensource gnucash work too.

---

### Post by FWSquatch on 2009-01-04
I have a very similar problem.  I am using Wachovia and it can connect, but doesn't seem to handle the response from the bank correctly.

```
10:59:52
Resolving hostname "pfmpw.wachovia.com" ...
10:59:52
IP address is 169.200.182.181
10:59:52
Sending request...
10:59:52
Connecting to bank...
10:59:56
Connected.
10:59:56
Waiting for response...
10:59:57
HTTP-Status: 200 (OK)
10:59:57
Parsing response...
10:59:57
Parsing response
10:59:57
Status for signon request: Success (Code 0, severity "INFO") The server successfully processed the request.
10:59:57
Status for account info request: Success (Code 0, severity "INFO") The server successfully processed the request.
10:59:57
Error parsing response
10:59:57
Finished. You may close this window.
```

Trying to use the online actions then crashes gnucash.

---

### Post by thomasaaron on 2009-01-05
Our accounting guy uses it with some success but says it is problematic. Here are some set-up instructions that might help you guys get it sorted out...

GnuCash online banking module instructions (aqbanking):
[http://wiki.gnucash.org/wiki/AqBanking](http://wiki.gnucash.org/wiki/AqBanking)



OFX settings:
[http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings](http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings)



Bank setting lookup:
[http://ofxblog.wordpress.com/](http://ofxblog.wordpress.com/)

Wachovia set-up instructions:
[http://ofxblog.wordpress.com/2007/05/28/ofx-fi-details-for-wachovia-bank-2/#comment-1495](http://ofxblog.wordpress.com/2007/05/28/ofx-fi-details-for-wachovia-bank-2/#comment-1495)

---

### Post by eyecreate on 2009-01-17
I have tried the settings from those blogs and areas with no real avail. It seems my bank, despite being on the blog, does not seem to like gnucash, which is sad because I like how it works compared to others, including moneydance. Are there no other suggestions? Should I bug report this? To where if so?

---

### Post by thomasaaron on 2009-01-17
Here, I believe...

[https://bugs.launchpad.net/ubuntu/+source/gnucash](https://bugs.launchpad.net/ubuntu/+source/gnucash)

---

### Post by MountainX on 2009-01-17
Here is my idea:

1. Use Yodlee.com to aggregate all my bank accounts. It is the best I have seen yet.
2. Download all transactions from Yodlee to a CSV file whenever I want. It is very easy. And Yodlee automatically keeps everything up to date.
3. Convert the CSV file to OFX (or QIF).
4. Import all transactions into gnucash. Gnucash can do this easily.

The crucial feature for me is #3. I want to do it in one simple step that involves only a single file that gnucash has to import, even when the transactions represent many different accounts.

In a couple days I hope to have a simple application that will do this step. I plan to make it available as open source.

If anyone else is interested, reply here.

I think this is the best of all worlds - the power of gnucash with the online banking prowess of Yodlee.

---

### Post by eyecreate on 2009-01-17
Mountainx, your idea seems really good. It would be even cooler if you were able to integrate it somehow into gnucash so you can convert/import automatically. My one complaint might be that I'm really looking for a solution for one click update of my bank account info to gnucash, so that I don't have to do tedious work every day to download my statement from my bank(which I can already do from their site)and import any new items. That was one thing I liked about moneydance was it's oneclick idea, but I like how gnucash operates better. Wish for the best of both worlds. The fact that moneydance can do it, though should say there should only be a bug or something in gnucash's aqbanking preventing it from working. Also, when I try to use gnucash/aqbanking, there is a checkbox for "close window when done" that is enabled, but I can not uncheck it to see error info because as soon as it starts, it closes. Is there another way(preference file/menu) for me to keep the connection window up so I can see any errors?

---

### Post by MountainX on 2009-01-17
With Yodlee.com, you no longer have to do any tedious downloading of any of your bank statements, credit card statements, bills, etc. 

Yodlee is even better than "one click". It will update all your transactions, account balances, etc. with zero clicks. You can use it daily to keep an eye on things.

But then when you want more powerful reporting, use gnucash. It is easy to download ALL your data from Yodlee. You don't have to go to a bunch of different web sites for banks, credit cards, etc.

And when you have all those transactions in gnucash, you can make any reports and do any budgeting you want to do.

So the only catch is transforming Yodlees downloaded CSV file to an OFX or QIF file that gnucash can easily read. I should have a solution for that shortly. (And if you only have one or two accounts, you can do it already with Calc2Qif. My solution will make it easy for any number of accounts.)

---

### Post by bradhaack on 2009-01-18
I think that's a great idea (yodlee -> gnucash).  I gave gnucash a try last yr and gave up because of the failure of the download tools & I'm giving it another try, but it doesn't appear that it's any better than it was a yr ago.  I think that OFX would be better than QIF, but I'm no expert.

---

### Post by MountainX on 2009-01-21
> **bradhaack said:**
> I think that's a great idea (yodlee -> gnucash).  

OK, we have now set up a project for [csv2ofx]("http://github.com/mulicheng/csv2ofx/tree/master") at github.

This is a python app (tested on Ubuntu 8.04) that will convert the Yodlee CSV format to OFX. GnuCash can read the OFX file. 

This means you can use Yodlee to aggregate all your accounts and handle all the electronic downloads. Yodlee updates the accounts automatically and it handles far more banks than any other personal financial management software I have used.

With Yodlee you can download a CSV file of all your transactions (for any period of time, from a week to the entire history in Yodlee).

Then you can use csv2ofx to read all those transactions into GnuCash. GnuCash gives you the reporting and budgeting capabilities that Yodlee doesn't. 

I think it is the best of both worlds. Finally, I have a replacement for MS Money that is better than MS Money (or Quicken or anything else I have tried in the past). Money was my last Windows app. I'm now 100% Ubuntu! :)

The link for csv2ofx is here: [http://github.com/mulicheng/csv2ofx/tree/master](http://github.com/mulicheng/csv2ofx/tree/master)

The best way to get the project is to use "git". The "git clone" link (which creates a local project for you) is available at the link above. But I'll list it here too:
```
git clone git://github.com/mulicheng/csv2ofx.git
``` 

If you don't use git yet, on Ubuntu, you can simply add it via Synaptic Package Manager. Then paste the git clone line from above in a terminal.

If you are not familiar with git, you can [download an archive]("http://github.com/mulicheng/csv2ofx/") of the contents.  If you use git however, and the developer(s) make a change, you'll easily be able to update (just type "git pull" in a terminal from the csv2ofx directory).

After you retrieve the files, you can run the program directly from the source files:

./csv2ofx

If you would like, you can install the package on your system like this:
(Assuming Ubuntu, run this from /home/your-user/csv2ofx)

```
sudo python setup.py install
```

If you do this, you should get the csv2ofx script installed somewhere in your path and be able to type:

```
csv2ofx
```

from any directory.

A note on mappings. The mappings.py file is extremely flexible. Currently it is optimized for Yodlee's CSV format.

One final note.

The GUI is programmed with wxPython.  On Linux wxPython is wxGTK.  Some distributions name the package wxPython and some wxGTK.  Either way, you may need to use apt (or Synaptic) to install the package if it isn't on your system. There are no other dependencies (as far as I know).

---

### Post by eyecreate on 2009-01-22
This looks cool, I will have to test it out sometime soon.

---

### Post by bmcclure on 2009-04-10
I am a new Ubuntu user trying out Intrepid Ibex Ubuntu 8.10.  I am also new to Gnucash and NOT a Programmer.  I would really appreciate someone taking a look at how I have tried to modify the mappings.py file (into csv2ofx_custom.py) for csv2ofx file to import my Discover Credit Card Info via OFX.  All I seem to get is a blank ofx file.  Also I am not really worried about the qif format.
I added the following lines after the yodlee and cu lines:

disc = {
    'OFX':{
        'skip':lambda row,grid: fromCSVCol(row,grid,'Trans. Date'),
        'BANKID':lambda row,grid: 'Discover',
        'ACCTID':lambda row,grid: 'My Account',
        'DTPOSTED':lambda row,grid: toOFXDate(fromCSVCol(row,grid,'Post Date')),
        'TRNAMT':lambda row,grid: fromCSVCol(row,grid,'Amount'),
        'FITID':lambda row,grid: row,
        'PAYEE':lambda row,grid: fromCSVCol(row,grid,'Description'),
        'MEMO':lambda row,grid: fromCSVCol(row,grid,'Category'),
        'CURDEF':lambda row,grid: 'USD',
        'CHECKNUM':lambda row,grid: row,
    },

# And I changed the following to:

all_mappings = {Yodlee':yodlee, 'Credit Union':cu, 'Discover',disc}


I am trying to get this to work with the following file csv file format

Trans. Date   Post Date   Description   Amount     Category
01/01/2009    01/02/2009  Safeway       15.44      Supermarkets 

Any help would be appreciated.

---

### Post by MountainX on 2009-04-11
> **bmcclure said:**
> 

Any help would be appreciated.

From Dennis:
He's probably getting a blank OFX file because of the skip field.  It should simply be:
```

...
'OFX': {
'skip': lambda row,grid: False,
....

```
Which would instruct that mapping to not skip any fields.

As a side note though: GnuCash, via aqBanking, can import OFX data directly for Discovercard.  Discover supports online banking for free.

---

### Post by lisati on 2009-04-13
Two comments:

1. Based on my own observations, the OFX file format seems to be best suited to one account per OFX file.

2. Probably irrelevant to this discussion: I would have thought that using CSV files might present some challenges if you use more than one bank: the three banks I use fill in the details differently. (This is a nuisance but can be worked around).

---

### Post by bmcclure on 2009-04-15
Thanks MountainX,

Unfortunately this didn't work.  The files still come out blank.  A little more information, when I originally import the csv file, I have the click on the upper left square for it to show up within the csv2ofx program.  Also, I was trying to get this to work with Discover which has fewer fields, before I try it with my own credit union.  My credit union does not offer OFX.  Also, I am having trouble with Aqbanking set up for Discover, but I will write that in another post/forum instead.

---

### Post by MountainX on 2009-04-15
Can you upload a sample of your CSV file? Make sure you remove any personal info.

---

### Post by bmcclure on 2009-04-17
Here is the csv file.  I have temporarily renamed the file extension to txt so that I can attach it.

---

### Post by MountainX on 2009-04-18
> **bmcclure said:**
> Here is the csv file.  I have temporarily renamed the file extension to txt so that I can attach it.

I forwarded your csv file to the developer. Let's see what he can suggest.

---

### Post by MountainX on 2009-04-24
> **MountainX said:**
> I forwarded your csv file to the developer. Let's see what he can suggest.
Here is the reply from Dennis. (BTW, check out the github for this project here:
[http://github.com/mulicheng/csv2ofx/tree/master](http://github.com/mulicheng/csv2ofx/tree/master))

I'm so sorry for taking so long.  I've been swamped this week and didn't feel good a couple of the days.  Anyway, I'm trying to catch up.

There are a couple issues with the Python sent below.  Here is a modified version that worked for me:

```
# add to home directory/csv2ofx_custom.py 
# I commented the issues I found
disc = {
'OFX':{
# the skip value should just return False.. You don't want to skip any rows
'skip':lambda row,grid: False,

 'BANKID':lambda row,grid: 'Discover',
'ACCTID':lambda row,grid: 'My Account',
'DTPOSTED':lambda row,grid: toOFXDate(fromCSVCol(row,grid,'Post Date')),
'TRNAMT':lambda row,grid: fromCSVCol(row,grid,'Amount'),
'FITID':lambda row,grid: row,
'PAYEE':lambda row,grid: fromCSVCol(row,grid,'Description'),
'MEMO':lambda row,grid: fromCSVCol(row,grid,'Category'),
'CURDEF':lambda row,grid: 'USD',

 # CHECKNUM I changed to return a string, csv2ofx didn't like an int here
'CHECKNUM':lambda row,grid: str(row),
}
# needed one more } here
}


all_mappings = {'Yodlee':yodlee, 'Credit Union':cu, 'Discover':disc}


 # was .... 'Discover',disc... the "," should be ":"... and was invalid syntax

# 
```I found these errors by looking at the console when csv2ofx starts.  It prints if there is syntax errors in your custom file.  Once I fixed these, I imported/exported the sample csv file without any issues.

Best Wishes
-Dennis

---

### Post by bmcclure on 2009-05-07
Thanks for all the help Mountain X.  This finally gave me a file that Gnucash could import.

Then I ran into a new and unusual problem.  Each of my files usually spans from about the 16th of one month to  the 15th of the next.  When I try to bring the OFX files into Gnucash it cuts off about the first 8-10 days of records in each file.  So instead of starting on the 16th the records start around the 24th to 26th.  It looks like a Gnucash problem as I have opened up the OFX files and can clearly see the earlier entries that become missing upon import to Gnucash.  It's a puzzler.

But thanks again fo the conversion help.

---

### Post by MountainX on 2009-05-07
Glad you got the conversion working. I have not experienced the gnucash problem you describe. I have imported a lot more than a month's worth of data. But there are a couple gnucash support venues (such as the mailing list) that will probably help you resolve that. Good luck!

---

### Post by amanda on 2009-08-06
> **MountainX said:**
> 
The GUI is programmed with wxPython.  On Linux wxPython is wxGTK.  Some distributions name the package wxPython and some wxGTK.  Either way, you may need to use apt (or Synaptic) to install the package if it isn't on your system. There are no other dependencies (as far as I know).

I got this running at home months ago but find myself wanting the same at the office and it isn't working. 

[0 amanda@stillwell csv2ofx]$ sudo python setup.py install 
worked fine, to all appearances, but when I try to run

[0 amanda@stillwell csv2ofx]$ ./csv2ofx 
Traceback (most recent call last):
  File "./csv2ofx", line 10, in <module>
    import csv2ofx
  File "src/csv2ofx/__init__.py", line 5, in <module>
    import wx
ImportError: No module named wx

My guess is that I'm missing ye olde wxPython or wxGTK but I'm not sure which package to choose to install it. Ideas? Should I just stab about in the dark until I hit something?

---

### Post by MountainX on 2009-09-10
> **amanda said:**
> 
My guess is that I'm missing ye olde wxPython or wxGTK but I'm not sure which package to choose to install it. Ideas? Should I just stab about in the dark until I hit something?

In Jaunty, I used python-wxgtk2.8 and I installed with Synaptic.

---

### Post by reubano on 2009-11-23
MountainX, thanks for the script. I was able to use it to generate an OFX file perfectly. However, I wish to automate the process in a php script that will download a csv file from mint and then process it with csv2ofx. How can I call csv2ofx from within a php script so that I don't have to use the gui? Thanks!

Reuben

P.S. if anyone wants a copy of my custom mint mappings, let me know.

---

