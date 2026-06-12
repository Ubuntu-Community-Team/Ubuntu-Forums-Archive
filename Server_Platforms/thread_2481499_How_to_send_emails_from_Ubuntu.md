---
title: "How to send emails from Ubuntu"
date: 2022-12-01
forum: Server Platforms
---

### Post by fernandoch on 2022-12-01
Hello,

How to be able to send emails from Ubuntu for my wordpress websites?

Thanks

---

### Post by LHammonds on 2022-12-01
That's a loaded question.  There are a great many ways but what way are you expecting it to work?  Meaning, what mail server are you expecting to use to pass off email to deliver for you?

If you have no mail server, you will need to use one hosted elsewhere or create your own mail server.

Using one hosted elsewhere (like gmail) will require knowing how that host expects you to interact with it...such as connectivity requirements, credentials, etc.  Then you just need to use a mail sender to interface between your web app and the destination mail server.  I tend to use the very lightweight program called sSMTP.  I wrote a tutorial for myself a while back on how to do this...which I had all my servers send email to my internally-hosted mail server.  [Setup Server for Sending Email using sSMTP](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=257)

If you are going to setup your own email server, well, I cannot help you there.  It is a complicated process and requires a depth of information in various areas and should be considered a very advanced topic.

LHammonds

---

### Post by mIk3_08 on 2022-12-03
> **fernandoch said:**
> Hello,

How to be able to send emails from Ubuntu for my wordpress websites?

Thanks
I don't really know what you mean by sending email but if you are about to use your website domain name as your mail service address, As LHammonds said its a loaded questions. It really depends on your web hosting. If your are using Cpanel in your hosting then it will be easy then. And setting up email alias is not that hard but if not, Its way to long process to do it. If you are to build mail server, and you don't have any idea of it my advised is to hire someone that is capable of doing on web services and can deliver what you wanted. Because if you want to do it on your own and you don't have any background on it, again, Its a long way process to do it. Regards and cheers.

---

