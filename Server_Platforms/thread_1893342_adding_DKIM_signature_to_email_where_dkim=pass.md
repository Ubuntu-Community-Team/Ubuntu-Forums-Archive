---
title: "adding DKIM signature to email where dkim=pass"
date: 2011-12-10
forum: Server Platforms
---

### Post by jeevandongre on 2011-12-10
Hi,
I am building a e-mailing app and I am using Amazon SES API to send emails and long with that I am adding the DKIM signature to the email which are being sent. Presently the app is in the testing mode. I am able to send email but one thing I observed in the sent email is that the DKIM sign says dkim="hardfail" which is not a good thing. 

How do I configure the setting. I am running ubuntu 10.10 EC2 instance in production and ubuntu 11.10 locally.
I have used this GEM [https://github.com/jhawthorn/dkim](https://github.com/jhawthorn/dkim) to add DKIM Sign.

Its been already 2 days I am try to solve this issue, kindly help me out.

---

