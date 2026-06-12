---
title: "bash scripts"
date: 2009-05-20
forum: Server Platforms
---

### Post by Vegan on 2009-05-20
I want to stuff commands into a cron job.

fsck
badblocks -v /dev/sda

so should I wrap this in some tags:

<?bash
....
?>

---

### Post by HermanAB on 2009-05-20
The trick to remember is that Cron has a very limited environment, so cron bash scripts must always use the full path of each program it calls.  Otherwise, you can drop any bash script into /etc/cron.hourly (daily, weekly, monthly...) and it will execute.

---

### Post by Vegan on 2009-05-20
hmmm, running fsck manually and 4 orphan files

running badblocks -v /dev/hda and tons of problems

so much for this disk

---

