---
title: "Trying to build my own stock database"
date: 2011-08-23
forum: Server Platforms
---

### Post by Failboat88 on 2011-08-23
Looking for suggestions on what tools to use. I'm a finance major with limited programming knowledge. I would like to start collecting my own stock data. I would like to pull data from google finance or something similar. Also, I subscribe to data from AAII, American Asso. of Individual Investors, and would like to add that data into the database. and be able to have a nice gui to run queries on.

My interests are finding if there are various different arbitrage opportunities and fundamental value investments. 

Very low budget. Want to run it on ubuntu. I was looking at Postgre SQL as the database, but really have no idea what is optimal. Not to sure on the gui or how to pull the data.  

If anyone is interested in the topic and would like to help me set up and run algorithms let me know too.

---

### Post by oldfred on 2011-08-24
I retired 5 years ago and kinda knew MS Access. So I looked for how to do things in Linux. Since stocks was an interest I decided to see what was available. There are a lot of programs, some more sophisticated than others. I was looking for something simple, more just value & current prices. 

I ended up creating my own little python program using sqlite and gtk. But since I was just learning I am now trying qt for the gui. Neither work well enough that i would share at this time.

Take a look at qtstalker, jstock, trading monkey and I forget some others.

I have downloaded some of the spreadsheets from AAII, and was going to convert some to OpenOffice, but never got around to it.

---

### Post by Failboat88 on 2011-08-24
Well if your still interested in investing. I'd be happy to collaborate. I've been working on screens in AAII. The price only updates weekly. I'd like to get real time screens that could notify when certain criteria are met. I don't know all the math behind stat arb, but I have always wanted to try and learn it. My focus is definitely fundamental investing. I'm not entirely sold on quantitative techniques.

---

### Post by oldfred on 2011-08-24
If you just want current(Yahoo is on 20 min delay) stock prices this works:

fred@fred-MavericDT:~/Projects/python$ python stockprice.py
{'jpm': '35.155', 'ibm': '163.9103', 'msft': '24.62', 'nok': '5.95'}

save as stockprice.py
```

import urllib 
symbols = 'ibm jpm msft nok'.split() 
quotes = urllib.urlopen( 'http://finance.yahoo.com/d/quotes.csv?s='+ 
          '+'.join(symbols) + '&f=l1&e=.csv').read().split() 
print dict(zip(symbols, quotes))

```

I thought I knew a little programing & wanted to learn python. So I said I will 'just' add a gui, maybe save to a sql database and read the list to stocks from a sql table and show it in a grid.
I did not know python, did not know gtk, knew a little sql and not being a real programmer had lots of 'fun' figuring out how to do just that. My gtk versions kinda works, I can import a text file of stocks to a table, update from Yahoo & display current price info.

---

### Post by robgr85 on 2011-08-25
> **Failboat88 said:**
> Looking for suggestions on what tools to use. I'm a finance major with limited programming knowledge. I would like to start collecting my own stock data. I would like to pull data from google finance or something similar. Also, I subscribe to data from AAII, American Asso. of Individual Investors, and would like to add that data into the database. and be able to have a nice gui to run queries on.

You can allways create bash script, that will scan and collect informations from Your sources at regular basis, but writing php app would seem to be a bit better and reliable idea (If You can get data in xml or csv format).

And a bit off topic question - do stock professionals often use data mining techniques?

---

### Post by RandomProgrammer on 2011-08-25
Have you considered using LibreOffice Calc to do this? There's a free plugin for OpenOffice (works with LibO) called "GetQuote" that will let you retreive different kinds of data about a particular stock. You can pull that data right into your spreadsheet and, of course, manipulate it in any way you want.

Just a thought!

Anthony

---

### Post by Failboat88 on 2011-08-27
And a bit off topic question - do stock professionals often use data mining techniques?[/QUOTE]

I have read that larger funds mine all kinds of data. They even mine articles to try and figure how the general population perceives a stock.

They probably don't mine quotes off google finance. There is subscriptions to live or historical data. A bloombox cost over 1000 per month. A year of option data can cost 700 dollars.

---

