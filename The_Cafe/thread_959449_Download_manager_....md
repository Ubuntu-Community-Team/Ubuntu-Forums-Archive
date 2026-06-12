---
title: "Download manager ..."
date: 2008-10-26
forum: The Cafe
---

### Post by Diptansu on 2008-10-26
An 1.8 GB download is being stopped in the middle. Some ppl told me a proper download manager would help. what is the best download manager for Ubuntu? Do I really need a 'DM' to solve the problem?

---

### Post by billgoldberg on 2008-10-26
> **Diptansu said:**
> An 1.8 GB download is being stopped in the middle. Some ppl told me a proper download manager would help. what is the best download manager for Ubuntu? Do I really need a 'DM' to solve the problem?

Firefox 3 can resume downloads, or so I believe.

So unless the source of the download is gone, you should be able to restart the download.

If you really want a download manager, I have used these and had no problems with them:

- gwget
- aria download manager

I prefer gwget.

---

### Post by xpod on 2008-10-26
I like the DownThemAll Firefox extension myself.
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by Barrucadu on 2008-10-26
I like wget - but firefox and opera can resume downloads, so in 90% of cases you'll be able to resume it through your browser.

---

### Post by ice60 on 2008-10-26
you can finish the download with wget. if it's on your desktop you can run this -
```
cd ~/Desktop && wget -c *"the name of the file"*
```

---

### Post by mips on 2008-10-27
Aria2 or wxDownload Fast

---

### Post by gn2 on 2008-10-27
> **xpod said:**
> I like the DownThemAll Firefox extension myself.
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

+1 for DownThemAll, couldn't live without it.

---

### Post by FuturePilot on 2008-10-27
D4x

---

### Post by Vishal Agarwal on 2008-10-27
for Big size downloads I like the wget. It provides no of switched, out of those --retry-connrefused and --limit-rate are very useful.

---

### Post by Diptansu on 2008-10-27
Thanks to all you guys ...

I surely try out these softwares. Can I use 'apt-get' to install these? Or ...

Well, I made a mistake and thats why you misunderstood my problem a bit. The download its not actually being 'stopped' in the middle of it . it actually showing it is 'done', but the size it has downloaded is 154 MB or 390 MB ... while the original file size was 1.8 GB. So, there isn't any option to resume it. Because it is saying its already done. But it didn't download the entire file (1.8 GB).

Thanx again ... :)

---

### Post by bigbrovar on 2008-10-27
i actually use wget (a commandline download tool..) for for a gui u can try multiget .. its very powerful and can and easy to use.. very close to download manager on windows  [http://www.getdeb.net/app/MultiGet](http://www.getdeb.net/app/MultiGet)

---

### Post by t0p on 2008-10-27
I would advise you to stay clear of the firefox addon **DownloadHelper** (aka **VideoDownloadHelper**).  The addon does make it easier to download videos from streaming sites... but it's also a load of rubbish.

IMHO.  YMMV.

---

### Post by dixon on 2008-10-29
[fatrat]("http://fatrat.dolezel.info/")

---

