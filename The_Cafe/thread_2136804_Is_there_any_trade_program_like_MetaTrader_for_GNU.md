---
title: "Is there any trade program like MetaTrader for GNU/Linux?"
date: 2013-04-18
forum: The Cafe
---

### Post by woxuxow on 2013-04-18
Is there any trader program like MetaTrader for GNU/Linux?

---

### Post by Old_Grey_Wolf on 2013-04-18
Are you asking about the MetaTrader server program the broker runs or the client software the broker's customer runs?

The MetaTrader client software must be supported by the broker. If you are a customer, ask your broker what other Linux clients they support. 

If you are only looking for stock charting, you can get similar charting capabilities of MetaTrader using a Linux program; such as, [QTstalker]("http://qtstalker.sourceforge.net/#screenshots"). QTstalker does not allow you to place orders with your broker using the application nor does it provide real-time streaming of prices. You have to update the stock data periodically from one of the data sources and some sources only update their data at the end of the trading day. The stock market you trade in may not offer stock data that QTstalker can access.

---

### Post by woxuxow on 2013-04-19
> **Old_Grey_Wolf said:**
> Are you asking about the MetaTrader server program the broker runs or the client software the broker's customer runs?

The MetaTrader client software must be supported by the broker. If you are a customer, ask your broker what other Linux clients they support. 

If you are only looking for stock charting, you can get similar charting capabilities of MetaTrader using a Linux program; such as, [QTstalker]("http://qtstalker.sourceforge.net/#screenshots"). QTstalker does not allow you to place orders with your broker using the application nor does it provide real-time streaming of prices. You have to update the stock data periodically from one of the data sources and some sources only update their data at the end of the trading day. The stock market you trade in may not offer stock data that QTstalker can access.

Hi
I`m looking for a program that able me to follow the real-time streaming of prices and let me analyze charts
I don`t want to trade.

---

### Post by Mikeb85 on 2013-04-19
> **MustafaJF said:**
> Hi
I`m looking for a program that able me to follow the real-time streaming of prices and let me analyze charts
I don`t want to trade.

Real-time streaming is tough, because most services charge money for real time feeds.  

If you just want to analyse charts, Yahoo and Google's websites are surprisingly capable.  QTStalker is ok, but I prefer broker tools or websites.  The R programming language + RStudio is a great tool, but requires some programming know-how and work on your part.  But you can scrape information from websites, and make charts and analyse them pretty easily.

---

### Post by HermanAB on 2013-04-20
Merchant of Venice for example.  There are many.
[http://mov.sourceforge.net/](http://mov.sourceforge.net/)

---

### Post by woxuxow on 2013-04-21
Thanks everybody
I'll try Venice and QTstalker out
They sound great

---

### Post by MetaTraderProgramming on 2013-05-24
Not exactly, but it is possible to run MetaTrader 4 in Linux.
All you have to do is install WINE and then install MT4.[


> **woxuxow said:**
> Is there any trader program like MetaTrader for GNU/Linux?

---

