---
title: "Standard application for information gathering?"
date: 2012-04-21
forum: The Cafe
---

### Post by abyrne on 2012-04-21
Hi all,

   I've been wondering if there's ever been a widely agreed upon standard for gathering information to solve a problem (collecting various logs, config files, command outputs, etc). I did find [inxi]("http://code.google.com/p/inxi/") which looks like a tremendous little script, but I haven't found very many people using it on the Forums (maybe I'm just not looking hard enough).

  I came across this subject when I was trying to gather some data off a headless server that had lost network access due to a driver issue. Using udev rules, I was able to create a little script to copy some key logs onto a USB drive automatically upon plug-in. And while inxi works well, it doesn't collect log or config files. Anyway, I released a more polished version of the script I created [on my site]("http://abyrne.me/tutorials/2012/04/introducing-general-automatic-diagnostic-script-gads-v1-1/"), if anyone's interested.

But is there already a standard application for this kind of thing? If not, implementing one may really help the problem-solvers on the Forums.

---

### Post by SeijiSensei on 2012-04-22
[Logwatch](https://help.ubuntu.com/community/Logwatch) is a convenient reporting tool that summarizes most logs from syslog and emails you the report.  Typically it runs daily from cron.

It sounds like you want more than this, but it's a start.  Searching Google for "syslog report" and similar phrases brought up a lot of options.

---

