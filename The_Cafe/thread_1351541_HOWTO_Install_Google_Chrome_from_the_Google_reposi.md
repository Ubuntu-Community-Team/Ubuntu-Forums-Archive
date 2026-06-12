---
title: "HOWTO: Install Google Chrome from the Google repository"
date: 2009-12-10
forum: The Cafe
---

### Post by gletob on 2009-12-10
This is a guide for those that want to install the new Google Chrome Beta, and be able to update it through apt.

First add the google repo to the end of your /etc/apt/sources.list file as root.
```
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free main
```Now add the package signing key by running:
```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```Now run
```
sudo apt-get update
```Now to actually install the Google Chrome Beta run
```
sudo apt-get install google-chrome-beta
```And that's it!  Now you can run Google Chrome from you Application>Internet menu or by running google-chrome in the terminal.

---

### Post by NoaHall on 2009-12-10
Chromium is better. But still, nice guide.

---

### Post by cariboo on 2009-12-10
The Chrome install creates a cron job that goes out and checks the Google Chrome repository daily, so there is really no need to add it to your /etc/apt/sources.list

I agree I like the Chromium better, but the one thing I can't do is edit tags without having to right-click and open the editor in another tab. That can get real old after you've done it a dozen or more times a day

---

### Post by Tibuda on 2009-12-10
If you install the official deb from google, it already adds the google repository to your sources.list.d directory.

```
$ cat /etc/apt/sources.list.d/google-chrome.list 
deb http://dl.google.com/linux/deb/ stable main

```

Opera also does the same.

---

### Post by peterroots on 2010-03-15
The difference being that opera repositories work and google does not - apt-get update takes forever and finally times out on the google repositories added by the google chrome install. I have had google chrome installed for a week or two (on three machines) and none pick up the repositories from google (Kubuntu9.10)

---

### Post by rifter on 2010-03-24
> **gletob said:**
> This is a guide for those that want to install the new Google Chrome Beta, and be able to update it through apt.

First add the google repo to the end of your /etc/apt/sources.list file as root.
```
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free main
```Now add the package signing key by running:
```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```Now run
```
sudo apt-get update
```Now to actually install the Google Chrome Beta run
```
sudo apt-get install google-chrome-beta
```And that's it!  Now you can run Google Chrome from you Application>Internet menu or by running google-chrome in the terminal.

Actually you need to put 

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```

Otherwise you get errors like this:

```

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

```

Otherwise a perfect howto! :D

---

### Post by nindrianto on 2010-09-18
Thanks, still confuse in this way, cause I am newbie in linux. But I success to install chromium browser from Ubuntu Software Center. Just sharing...thanks.:P

---

### Post by portly on 2013-05-06
so much for that "howto" working.........

> W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

Oh well, back to the drawing board

---

### Post by oldos2er on 2013-05-06
Old thread closed.

---

