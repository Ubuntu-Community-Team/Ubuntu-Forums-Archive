---
title: "Owncloud - unable to log in to online account"
date: 2016-10-27
forum: Ubuntu Phone and Tablet
---

### Post by dom134 on 2016-10-27
Hello, I have just flashed Ubuntu touch onto a Meizu Pro 5.  I keep my contacts and calendar on a nextcloud server I have running at home using https via a Comodo certificate.  I am hoping to keep the calendar and contacts synched on the phone using the accounts > ownCloud settings; however when I put my url in:
> [https://www.dom134.com/nextcloud](https://www.dom134.com/nextcloud)
It comes up with
> Invalid host URL
I can access my nextcloud files from the phone's browser, but intriguingly when I try to download a file, it just hangs on the download page.  I am able to download files from other sites.

Does anyone have any ideas?

---

### Post by sitongia on 2016-10-29
I quit trying to use the accounts system setting for calendar, and it doesn't have contacts. I use the command line, like a number have suggested. For example,
[http://askubuntu.com/questions/616081/ubuntu-touch-add-contact-list-and-calendars](http://askubuntu.com/questions/616081/ubuntu-touch-add-contact-list-and-calendars)
You run the script on the phone in a shell to sync with owncloud. Tedious, but I think necessary, at this time.

Many core apps in Touch are close to being complete. It will be great when it is done. I think it's a great system.

---

### Post by dom134 on 2016-10-30
Thanks for that, I had not seen that; I certainly will be using it.
I managed to get the online account to connect by ammending my server:
> SSLCipherSuite RC4-SHA:AES128-SHA:HIGH:!aNULL:!MD5
SSLHonorCipherOrder on

---

### Post by aevare on 2016-11-03
This is one of the things I miss the most in Ubuntu, I created an owncloud account, but there is no contact sync and calendar sync hardly works, doesnt seem to pick up all the calendars.

Is it possible to create an app that just calls syncevolution?

---

