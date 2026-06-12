---
title: "Passwords.txt file in Chromium"
date: 2021-09-28
forum: Security
---

### Post by phil68 on 2021-09-28
[INDENT]I found a file named Passwords.txt on my desktop. I'm running Ubunut 18.04.6  (64 bit)  GNOME 3.28.2.  Location of the txt file is Home/snap/chromium/common/chromium/ZxcvbnData/1

The file has 30,000 entries such as those listed below and a number of vulgar terms. I deleted the file and emptied the trash - the file was deleted. I then restarted the system and searched for the file and it was not present. Then, when I executed the Chromium browser, the password text file was back. It's properties showed it was put out on the system when I executed Chromium. There are other suspicious txt files in the noted directory as well. Seems to be a list of possible passwords a cracker could use. Anyone have a handle on what these files represent? Are they legitimate and come with the Chromium browser?   FYI I found similar concerns on the apple forum about Chromium.

123456
password
12345678
qwerty
123456789
12345
1234
111111
1234567
dragon
123123
baseball
abc123
football
monkey
letmein
shadow
master
696969[/INDENT]

---

### Post by CharlesA on 2021-09-28
That sounds normal. Those are all super weak passwords.

zxcvbn is a password strength [s]checker[/s] estimator.

[https://github.com/dropbox/zxcvbn](https://github.com/dropbox/zxcvbn)

It was added back in 2020:
[https://chromium.googlesource.com/chromium/src/components/metrics/+/d59e49b0732b95cf05357db68bdf0ecd0211a0c1](https://chromium.googlesource.com/chromium/src/components/metrics/+/d59e49b0732b95cf05357db68bdf0ecd0211a0c1)

---

### Post by phil68 on 2021-09-28
Charles, thank you for the information and quick turnaround!

---

