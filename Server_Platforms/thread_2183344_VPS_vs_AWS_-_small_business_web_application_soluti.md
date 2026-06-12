---
title: "VPS vs AWS - small business web application solution needed"
date: 2013-10-24
forum: Server Platforms
---

### Post by garfonzo on 2013-10-24
I have built a web application for the company I work for - under 10 users. The web application runs their entire company - everything from estimates, scheduling, accounting, client management, etc. so they are on it all day. It's running Django with a MySQL backend. It's not a large DB from industry standards (probably under 1 million records now) but it will grow over time. Currently this web application is running on a server which sits in the office. If that one goes down, I have a second server in a different location (geographically) that runs the same web app as a standby.

I want to move this whole setup out of the office and onto a virtual setup for a variety of reasons. I'm looking at a VPS as a solution as it most closely resembles our current setup. But I'm also looking at Amazon's EC2 solution with an RDS (relational database service) connected to the EC2.

I'm wondering if going with Amazon's solution is too complex for our small needs or if the benefits available with AWS are worth employing. The pricing of Amazon's web service is close to that of a VPS, perhaps a little more, but there seem to be advantages with their services (easy backups, self healing nodes, etc.) that draw me to using them.

However, I'm also drawn to setting up a few "traditional" VPSs such as with Linode. A VPS may be more appealing possibly because this is familiar to me (AWS is new to me) but also because it might be a more logical choice based on our company size and user base/needs.

Any thoughts/direction on whether a VPS is better or whether something with AWS would be better?

Thanks for your input.

---

### Post by Habitual on 2013-10-24
VPS because the time, energy and finally cost (depending on your [motivation, desire, and willingness to learn]("http://https://aws.amazon.com/free/")) may far exceed the fixed cost of the VPS. 

Just my opinion.

---

### Post by garfonzo on 2013-10-24
> **Habitual said:**
> VPS because the time, energy and finally cost (depending on your [motivation, desire, and willingness to learn]("http://https://aws.amazon.com/free/")) may far exceed the fixed cost of the VPS. 

Just my opinion.


The more I research (after having posted this) the more I realize exactly what you've stated. AWS, while great for some, is likely over kill for our needs. 

Thanks for the input :)

---

### Post by Habitual on 2013-10-24
You are very welcome.

---

### Post by SeijiSensei on 2013-10-26
I'm a very happy Linode user, so I would recommend that approach.

However before you do this, you all need to sit down and discuss the security and privacy implications of moving these data out of the building.  Frankly if it were my private business records, client contacts, accounting data, etc., I'd keep them in-house.  You might consider a hybrid model where the public web server provides just the interface with all the MySQL data stored on a secure server inside the office.  I'd also suggest a simple OpenVPN [static-key tunnel]("openvpn.net/static.html&#8206;") with the internal server as the client connecting to the cloud server.  Then all the transactions between the cloud and your office are fully encrypted.

You could easily run this arrangement on a $20/month basic Linode.

Edit:  I wouldn't move your data to the cloud without talking to your attorney first either.  In the event of litigation, data on a server in your office may have greater legal protections than data sitting on an ISP's server in the cloud. You pay lawyers to worry about these things, then you get to decide whether to accept the risk.

Bottom line is that this is a business, not an IT, decision and needs to be treated as such.

---

### Post by sandyd on 2013-10-26
> **garfonzo said:**
> I have built a web application for the company I work for - under 10 users. The web application runs their entire company - everything from estimates, scheduling, accounting, client management, etc. so they are on it all day. It's running Django with a MySQL backend. It's not a large DB from industry standards (probably under 1 million records now) but it will grow over time. Currently this web application is running on a server which sits in the office. If that one goes down, I have a second server in a different location (geographically) that runs the same web app as a standby.

I want to move this whole setup out of the office and onto a virtual setup for a variety of reasons. I'm looking at a VPS as a solution as it most closely resembles our current setup. But I'm also looking at Amazon's EC2 solution with an RDS (relational database service) connected to the EC2.

I'm wondering if going with Amazon's solution is too complex for our small needs or if the benefits available with AWS are worth employing. The pricing of Amazon's web service is close to that of a VPS, perhaps a little more, but there seem to be advantages with their services (easy backups, self healing nodes, etc.) that draw me to using them.

However, I'm also drawn to setting up a few "traditional" VPSs such as with Linode. A VPS may be more appealing possibly because this is familiar to me (AWS is new to me) but also because it might be a more logical choice based on our company size and user base/needs.

Any thoughts/direction on whether a VPS is better or whether something with AWS would be better?

Thanks for your input.
If you are doing credit card work and are/or storing credit card info, I suggest you make sure that your provider/server can pass a PCI Compliance Audit before starting **anything**. Its one of the reasons why Amazon AWS is used - here is a list of PCI validations for their services [http://aws.amazon.com/compliance/pci-dss-level-1-compliance-faqs/](http://aws.amazon.com/compliance/pci-dss-level-1-compliance-faqs/). Note that having a PCI compliant host does not mean that your setup is instantly PCI Compliant; the infrastructure may be compliant but you have to make everything else compliant as well

Also - take a look at Rackspace to see if they suit your budget

---

