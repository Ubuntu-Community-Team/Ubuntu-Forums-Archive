---
title: "Blueprint: Bootloader integration testing"
date: 2012-05-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-05-15
There's another interesting Blueprint [COLOR="Red"]**_[here]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-q-grub-integration-testing")_**[/COLOR].

Just as [COLOR="Red"]**_[the one I posted before]("http://ubuntuforums.org/showthread.php?t=1980069")_**[/COLOR] (about Jockey and drivers), this one is also on something we've been talking for ages. There's some potential for improvement.

Regards,
Effenberg

---

### Post by kaldor on 2012-05-15
This cycle is going to be interesting :-)

---

### Post by grahammechanical on 2012-05-17
It looks to me that a lot of development time is going into producing automated tests. Perhaps Canonical will sell its services as a software testing lab.

Regards.

---

### Post by effenberg0x0 on 2012-05-17
> **grahammechanical said:**
> It looks to me that a lot of development time is going into producing automated tests. Perhaps Canonical will sell its services as a software testing lab.

Regards.

Indeed. I think it's a know fact that automated testing has some known problems (or limitations):

- It's impossible to test an entire OS
-- The time and effort involved in writing enough test scripts to test a whole OS, its applications, usage scenarios, would demand a large dedicated team. It's not viable for most software companies.
-- Some things just can be automated; 
-- Automation frequently fails to detect things human senses do;
- Test scripts break easily when software is updated;
- Even if you eventually reach a point in which a large part of the OS is being tested with automation, it's hard and time consuming to keep test scripts updated;
- Automated testing results are purely quantitative.  It has no qualitative info in most cases.

I think all software companies go through this phase, deploy many automated solutions, tried to have a huge pool of hardware in a lab to run the automated tests, etc. From a business point of view, it looks like a less expensive option than investing in (and dealing with) real people. 

In my opinion, this strategy breaks down in a couple releases. If there was a bulletproof, almost magic, solution to allow software companies to drop humans and rely exclusive on automation (reaching similar or better results), make no mistake Microsoft, IBM, Oracle, SAP, etc software would have no bugs. They have the resources to deploy all existing automated testing solutions and even create their own. 

The truth is that you can't have good software without investing on knowledge and training for human testers (employees - in the case of proprietary software, or community - in the case of open source). Nothing beats the human brain (yet).

Now, looking from a positive perspective, we do have room for automation: We know Ubuntu still gives a lot of importance to testing the installer and first boot (ISO-Testing). Although I can't see the point in ISO-Testing (versus package/application in-depth testing), ISO-Testing can and *should* be completely automated, freeing the community of testers from this process.  I'm all for ISO-Testing automation, instead of human mechanization processes. I'd love to see all ISO-Testing automated ASAP.

Regards,
Effenberg

---

### Post by ronacc on 2012-05-18
The reason automated testing breaks down is that no set of automated tests no mater how comprehensive can anticipate all of the possible uses ( and misuses ) that all potential users will put the system being tested to , and that applies not just to software .

---

