---
title: "Gathering data from the web"
date: 2005-10-26
forum: The Cafe
---

### Post by ecmerkle on 2005-10-26
Friends,

I am in the midst of moving from windows to ubuntu, and I am still learning the ins and outs of linux.  My apologies if this is a simple question or if it's inappropriate for this forum, but I haven't found a simple answer in my searches for this information.

What I want is a program that reads data from web pages and writes it to, say, a text file.  For example, one thing I would like to do is obtain sports statistics from web sites in real time, import the statistics to a spreadsheet, and perform manipulations on them.  Back when I used excel, there was an option called "web query" that didn't work too well but that was able to extract some data from tables in web sites.  Is there a linux equivalent to this?  I've read a little bit about using SQL and PHP for data manipulation, and I'm wondering if this is the best (and easiest) way to go.

Thanks,
Ed

---

### Post by BoyOfDestiny on 2005-10-27
[QUOTE=ecmerkle]Friends,

I am in the midst of moving from windows to ubuntu, and I am still learning the ins and outs of linux.  My apologies if this is a simple question or if it's inappropriate for this forum, but I haven't found a simple answer in my searches for this information.

What I want is a program that reads data from web pages and writes it to, say, a text file.  For example, one thing I would like to do is obtain sports statistics from web sites in real time, import the statistics to a spreadsheet, and perform manipulations on them.  Back when I used excel, there was an option called "web query" that didn't work too well but that was able to extract some data from tables in web sites.  Is there a linux equivalent to this?  I've read a little bit about using SQL and PHP for data manipulation, and I'm wondering if this is the best (and easiest) way to go.

Thanks,
Ed[/QUOTE]


Hmm, there should be something out there like that, maybe some sort of RSS reader just for data pages give it (news, weather, etc)... 

What I use for downloading pages/content, keeping it up to date etc, is wget.
If you have ubuntu installed you should have it already.

[http://www.gnu.org/software/wget/wget.html](http://www.gnu.org/software/wget/wget.html)

Hope this helps you.

---

### Post by 23meg on 2005-10-28
Bash will let you do that in a very customizable manner. Check the links from [this excellent bash site](http://www.shelldorado.com/) for lots of ready to go bash scripts, which you can modify a bit for your needs automate with cron/anacron.

Once you get accustomed to getting things done with bash you'll wonder how you lived without it.

---

