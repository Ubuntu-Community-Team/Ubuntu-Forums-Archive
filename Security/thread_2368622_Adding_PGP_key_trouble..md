---
title: "Adding PGP key trouble."
date: 2017-08-13
forum: Security
---

### Post by juan53 on 2017-08-13
Dear Ladies and Gentlemen

I write this post because recently I have tried to install GNU Ring. ( The website of the software tool: [https://ring.cx/en/](https://ring.cx/en/) ) I have followed the steps to install it, those are in the next link: [https://ring.cx/en/download/gnu-linux](https://ring.cx/en/download/gnu-linux)
Otherwise:

sudo sh -c "echo 'deb [https://dl.ring.cx/ring-nightly/ubuntu_16.04/](https://dl.ring.cx/ring-nightly/ubuntu_16.04/) ring main' > /etc/apt/sources.list.d/ring-nightly-main.list"
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys A295D773307D25A33AE72F2F64CD5FA175348F84
sudo add-apt-repository universe
sudo apt-get update && sudo apt-get install ring
The thing is when I have tried to add the PGP key, server does not answer to the request. So I think that the problem could well be in my firewall config. My question is, do you know which protocol is used to add PGP keys? In addition, could you tell me what you think that it might be the problem?

Thanks a lot in advance

---

