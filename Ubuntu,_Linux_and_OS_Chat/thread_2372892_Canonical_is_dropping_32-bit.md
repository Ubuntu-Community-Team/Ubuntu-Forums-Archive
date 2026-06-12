---
title: "Canonical is dropping 32-bit?"
date: 2017-09-29
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-09-29
I've been hearing that Canonical is dropping 32-bit support for Ubuntu, well, this is bad news for me, I have two 32-bit computers that runs wonderfully well, I have a Xubuntu desktop and a Lubuntu laptop, and I certainly don't want to throw them into the trash, I want to use them til their dead.

Will this affect Xubuntu and Lubuntu?

---

### Post by ian-weisser on 2017-09-29
A citation or link to what you've 'been hearing' would be helpful.
There's a lot of old FUD out there on the dirty, dirty internet.
And a lot of users misunderstand the true news.

It may not be as bad as you think.

---

### Post by ardouronerous on 2017-09-29
I found the story here:

[https://itsfoss.com/ubuntu-drops-32-bit-desktop/](https://itsfoss.com/ubuntu-drops-32-bit-desktop/)

---

### Post by vasa1 on 2017-09-29
There's a long and older thread here: [https://ubuntuforums.org/showthread.php?t=2312451](https://ubuntuforums.org/showthread.php?t=2312451)
and see [https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051](https://ubuntuforums.org/showthread.php?t=2372469&p=13691051#post13691051)

---

### Post by ian-weisser on 2017-09-30
It's NOT 'all Ubuntu flavors are abandoning all 32-bit forever.' Not even close.

You wrote that you run Xubuntu and Lubuntu...so you don't run the 'Ubuntu Desktop' (Unity) already anyway.
Re-read the article carefully with that understanding.

---

### Post by cariboo on 2017-09-30
The article also states that there won't be any i386 Ubuntu images (32-bit iso) it doesn't say anything about dropping support for 32-bit. The packages will still be in the repositories so you can still upgrade to 18.04 LTS when it becomes available, you just won't be able to do a fresh install.

---

### Post by ardouronerous on 2017-09-30
> **ian-weisser said:**
> It's NOT 'all Ubuntu flavors are abandoning all 32-bit forever.' Not even close.

You wrote that you run Xubuntu and Lubuntu...so you don't run the 'Ubuntu Desktop' (Unity) already anyway.
Re-read the article carefully with that understanding.

The part of the article that worries me is this:

> Other official Ubuntu flavors such as Xubuntu, Kubuntu, Lubuntu etc have not dropped 32-bit support **yet**

The yet part is what worries me.

> **cariboo said:**
> The article also states that there won't be any  i386 Ubuntu images (32-bit iso) it doesn't say anything about dropping  support for 32-bit. The packages will still be in the repositories so  you can still upgrade to 18.04 LTS when it becomes available, you just  won't be able to do a fresh install.

My preferred upgrade of choice is a fresh install, I've tried to upgrade from 12.04 to 14.04 and it gave me problems, so I really hope Canonical doesn't drop 32-bit ISOs for Xubuntu and Lubuntu.

---

### Post by ian-weisser on 2017-09-30
Don't worry about 'yet'.

A successful Ubuntu flavor on any architecture requires three things to succeed:
1) Community volunteers to test and document and provide support,
2) A compatible upstream kernel, and
3) A compatible upstream desktop stack.

Ubuntu (Unity) is being dropped because of #3 - nobody was willing to make Unity work well on 32-bit. If a dozen skilled volunteers magically appear tomorrow and start improving Unity on 32-bit, then the flavor is likely to return.

Lubuntu and Xubuntu are community-led, volunteer projects. They are not Canonical projects. You and your fellow 32-bit users are in control.

---

### Post by ardouronerous on 2017-09-30
> **ian-weisser said:**
> Don't worry about 'yet'.

A successful Ubuntu flavor on any architecture requires three things to succeed:
1) Community volunteers to test and document and provide support,
2) A compatible upstream kernel, and
3) A compatible upstream desktop stack.

Ubuntu (Unity) is being dropped because of #3 - nobody was willing to make Unity work well on 32-bit. If a dozen skilled volunteers magically appear tomorrow and start improving Unity on 32-bit, then the flavor is likely to return.

Thanks, that makes feel a whole lot better.:D

> **ian-weisser said:**
> Lubuntu and Xubuntu are community-led, volunteer projects. They are not Canonical projects. You and your fellow 32-bit users are in control.

Do you have any links or references to these? Thanks.

---

### Post by acheronuk on 2017-10-01
[https://twitter.com/LubuntuOfficial/status/913532513234096128](https://twitter.com/LubuntuOfficial/status/913532513234096128)

> Just to clear up any misconceptions, even though Ubuntu Desktop  is  dropping i386 (32 bit) ISOs, Lubuntu will continue to support  it.

> Lubuntu i386 support will continue as it always has.

As far as I know from Lubuntu people, they will continue to ship i386  builds and iso as long as the ubuntu infra allows. Ubuntu have not  announced the end for any technical capability for flavours in that  regard.

---

### Post by ardouronerous on 2017-10-02
Thanks for the info acheronuk :)

I'm glad Lubuntu will continue to support 32-bit computers, but what about Xubuntu though? Any word from them?

---

### Post by ian-weisser on 2017-10-02
Word about what?
The entire kerfuffle is about one package (unity)...that neither Xubuntu nor Lubuntu ever used,

---

### Post by flocculant on 2017-10-02
> **ardouronerous said:**
> Thanks for the info acheronuk :)

I'm glad Lubuntu will continue to support 32-bit computers, but what about Xubuntu though? Any word from them?

We're not doing anything regarding 32 bit currently.

---

