---
title: "Need help with exchange rate project involving mysql/postgresql and PHP"
date: 2009-07-17
forum: Server Platforms
---

### Post by Jago6060 on 2009-07-17
What I'm trying to do: Have a PHP(or shell) script that will run daily with cron to go out to a database that holds exchange rates, get the exchange rates for the day, then insert them into a mysql(or postgresql) database.

Where I'm stuck:  I can't seem to find a database out there where you can just connect anonymously to grab exchange rates. Figures I hit a wall before I really get going ](*,)

---

### Post by Wim Sturkenboom on 2009-07-17
Not sure where your problem is. In php, you use something like
```

$dbcnx=mysql_connect("localhost","username","password");

```
You don't want the username and password, I assume. Question is why not? What will be the difference between an anonymous user and a 'dummy' that you use to insert/update the exchange rates.

---

### Post by shredkingj on 2009-07-17
Instead of connecting to a database, how about a site that lists exchange rates?  Google Finance's main page has a listing of some major currencies: [http://www.google.com/finance](http://www.google.com/finance)

You could use wget from your shell script, and parse the data that you are looking for.  You would just have to keep an eye on this script because if Google (or whatever financial site you use) changes, you may have to modify your script.  Hope this helps.

---

### Post by Jago6060 on 2009-07-17
To Wim:  I know how to do a database connection via PHP.  My issue is who has a database that I can access either with a generic user or no user/password at all.

--------------------
My trepidation with parsing a web page is just as you mentioned, sites change, and I don't want to have to modify the script every time the site changes.  Another contributing factor is that I need exchange rates for some really odd currencies, so I was hoping to find one gigantic database with all(most) currencies.  I'm not really concerned with past exchange rates, but I want to be able to grab them on a daily basis and insert them into my database.

P.S. Thanks for the replies!

---

### Post by Wim Sturkenboom on 2009-07-17
Sorry, that was not quite clear to me.

---

### Post by grantemsley on 2009-07-17
It's extremely unlikely that someone is going to allow direct database access to such information (at least for free).

You might be able to find a site that offers an API instead, which returns the data in XML or whatever format they use, suitable for automatic parsing.

Quick google search brings up [http://finance.xaviermedia.com/](http://finance.xaviermedia.com/), which lets you get it via XML: [http://api.finance.xaviermedia.com/api/latest.xml](http://api.finance.xaviermedia.com/api/latest.xml) (your browser will probably format that nicely, use view source to see what you'd actually get in your php script).

This works much better than screen scraping a website, since it is immune to layout changes, as long as they keep the API available.

---

### Post by Jago6060 on 2009-07-20
Thanks for the input.  The project lead and I decided that what we're trying to do is much more effort than just a manual copy and paste.  TOPIC SOLVED/CLOSED

---

### Post by grantemsley on 2009-07-20
Personally I would consider using that API I linked to be the least effort way - might take an hour to setup, but you only have to do it once.

But to each his own...

---

### Post by Jago6060 on 2009-07-21
I think I'm going to give it a shot anyway on my own time.  I like having things automated, even if it takes some work.  I'll probably have more questions when it comes time to do the actual scripting.  On that subject, do you know of any good tutorials for shell scripting?

---

### Post by Jago6060 on 2009-07-25
~Bump~

---

