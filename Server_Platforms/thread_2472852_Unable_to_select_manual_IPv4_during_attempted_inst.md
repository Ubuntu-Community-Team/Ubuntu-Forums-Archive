---
title: "Unable to select manual IPv4 during attempted installation of 22.04 Jammy"
date: 2022-03-14
forum: Server Platforms
---

### Post by mdlueck on 2022-03-14
Greetings,

I am trying to beta test the daily Ubuntu Server amd64 ISO from last week (still have not gotten it to install) on a test machine. I wish to assign a static IPv4 address to the NIC. It sees our DHCP server and will accept an address from it. However when I adjust to manual IPv4, fill in the settings, it never stops the "Applying changes /" rotating progress animation.

The settings I put in for Manual IPv4 are as follows:

Subnet: 10.10.10.0/24
Address: 10.10.10.9
Gateway: 10.10.10.1
Name server: 10.10.10.10

Pushing Save blanked out the name server field, and it never finishes the "Applying changes" step.

We have a Class C IPv4 subnet. Addresses 10.10.10.1 through 10.10.10.254

Suggestions of something I got filled in incorrectly, or if not, then I will file a bug report.

** Oh, I just tried adjusting back to DHCP vs manual... now it also no longer picks up an address from our DHCP server. The spinning "Applying changes" attempting to test DHCP again.

I am thankful,

---

### Post by darkod on 2022-03-15
Not sure how the new version will work yet, but if you are literary putting 10.10.10.0/24 as a subnet mask that looks incorrect.

For the subnet mask there are various names that are used, but basically there are two types of formats. It would either be /24 (and in this case it usually goes together with IP address), or it will be 255.255.255.0.

In general the options are:

Option A:
IP address: 10.10.10.9
Subnet mask: 255.255.255.0

Option B:
IP address: 10.10.10.9/24
Subnet mask: not applicable because the /24 in the address tells it what the mask is

---

### Post by mdlueck on 2022-03-15
Greetings Darko,

The top question on the manual IP screen is Subnet which its help (once entering a mistake value) states "should be in CIDR form (xx.xx.xx.xx/yy)

So that field demands the /yy component to it.

The address field will not accept the "/" character being entered to it.

Subnet seems to be expecting a different value than Subnet Mask, which yes I agree for a full Class C would be 255.255.255.0

I am thankful,

---

### Post by darkod on 2022-03-15
OK, in that case the Subnet is the value that is also referred as Network, and yes, 10.10.10.0/24 would be correct value. As I said, I don't know the installer or how it looks.

It might be a bug, like you already said.

---

### Post by mdlueck on 2022-03-15
Greetings Darko,

Thanks for confirming it looks like my input is correct. I will write up a defect to report the unexpected behavior of both switching to manual / static IPv4, and also the inability to switch back to DHCP.

Reported here:
Jammy server installer unable to set IPv4 static nor switch back to DHCP
[https://bugs.launchpad.net/bugs/1964979](https://bugs.launchpad.net/bugs/1964979)

I am thankful,

---

