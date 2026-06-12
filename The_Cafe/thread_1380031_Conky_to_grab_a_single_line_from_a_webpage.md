---
title: "Conky to grab a single line from a webpage?"
date: 2010-01-13
forum: The Cafe
---

### Post by FatBoyNotSoSlim on 2010-01-13
Hi all,
I have tried to search for this, and considered posting it in the previous conky threads, but most were tailored towards screenshots and scripts.

Ok, a few weeks ago the website I was using to get exchange rate data from, switched off their RSS feeds, and I'm finally getting around to fixing it.

I havent found any new RSS feeds, but i did find that google has a nice clean page to get values.

I'm trying to pull the text "1 AUD = 0.9235 USD" from here: [http://www.google.com/finance/converter?a=1&from=AUD&to=USD](http://www.google.com/finance/converter?a=1&from=AUD&to=USD) .

i've tried directly calling wget with: ```
${execi 3600 wget -O - http://www.google.com/finance/converter?a=1&from=AUD&to=USD}
```
And even messed around with some conditions like 'tail' and 'cut' but its still showing the full html in my conky.

Googling for uses of wget with conky haven't worked, since a lot of guides are simply referencing how to install conky in the same post.

Any help would be greatly apreciated.

---

### Post by mobilediesel on 2010-01-13
> **FatBoyNotSoSlim said:**
> Hi all,
I have tried to search for this, and considered posting it in the previous conky threads, but most were tailored towards screenshots and scripts.

Ok, a few weeks ago the website I was using to get exchange rate data from, switched off their RSS feeds, and I'm finally getting around to fixing it.

I havent found any new RSS feeds, but i did find that google has a nice clean page to get values.

I'm trying to pull the text "1 AUD = 0.9235 USD" from here: [http://www.google.com/finance/converter?a=1&from=AUD&to=USD](http://www.google.com/finance/converter?a=1&from=AUD&to=USD) .

i've tried directly calling wget with: ```
${execi 3600 wget -O - http://www.google.com/finance/converter?a=1&from=AUD&to=USD}
```
And even messed around with some conditions like 'tail' and 'cut' but its still showing the full html in my conky.

Googling for uses of wget with conky haven't worked, since a lot of guides are simply referencing how to install conky in the same post.

Any help would be greatly apreciated.

Try this:
```
${execi 3600 wget -q -O - "http://www.google.com/finance/converter?a=1&from=AUD&to=USD"|grep "<div id=currency_converter_result>"|sed 's/<[^>]*>//g'}
```

---

### Post by FatBoyNotSoSlim on 2010-01-13
Worked perfectly, thank you.

---

### Post by GrouchyGaijin on 2010-12-27
Thanks - this was exactly what I was looking for.

---

### Post by sbjaved on 2012-02-12
Thankyou.

---

### Post by overdrank on 2012-02-12
Back to sleep thread. Thread closed.

---

