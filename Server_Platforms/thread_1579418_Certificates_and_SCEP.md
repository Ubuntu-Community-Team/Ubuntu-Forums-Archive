---
title: "Certificates and SCEP"
date: 2010-09-21
forum: Server Platforms
---

### Post by brettg on 2010-09-21
At my company all the suits are in a lather over getting iPhones to replace their existing Blackberry phones. The fact that iPhones are going to be a nightmare to manage for the IT Dept is not considered at all in the mad frenzy to get hold of the latest shiny toy. 

<sigh>

Therefore, I am required to produce a central management platform for distributing policy and configuration data to iphone users remotely.

Some research later and much to my surprise, this is not impossible, as the iphone supports a Cisco draft protocol called [SCEP]("http://en.wikipedia.org/wiki/Simple_Certificate_Enrollment_Protocol")

The problem is that there is next to zero information out there as to how to set this up.

What apple says:
> SCEP is designed to provide a simplified process to handle certificate distribution for
large-scale deployments. This enables Over-the-Air Enrollment of digital certificates on
iPhone that can then be used for authentication to corporate services, as well as enroll-
ment with a mobile device management server.
For more information on SCEP and Over-the-Air Enrollment, visit [URL="http://www.apple.com/
iphone/business/integration"]www.apple.com/
iphone/business/integration[/URL].

In reality, there is almost zero documentation on how to set this up, just glossy marketing brochures proclaiming how great it is.

Microsoft Server 2008 supports SCEP but I really don't want to go down that path at all. A few OSS projects claim to support it to varying degrees.

So, my question is, has anyone had any experience at all of setting up a certificate server under Linux? It doesn't have to be specifically using SCEP but it would need to have that capability. I'm looking at straight OpenSSL but I can't find any references to it supporting SCEP. In fact, I'm not sure that the SCEP support is even required at the certificate exchange part of the transaction. Actually I'm pretty confused about the whole thing.

Any input is most welcome. If I get something working I will put it in a howto for sure.

---

