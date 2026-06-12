---
title: "So what is a medium cve?"
date: 2022-12-14
forum: Security
---

### Post by donald187 on 2022-12-14
Ubuntu's definition is:
> 
Medium:  Open vulnerability that is a real problem and is exploitable for many users   of the affected software. Examples include network daemon denial of service,   cross-site scripting and gaining user privileges.


whereas a high cve is

> 
High:       Open vulnerability that is a real problem and is exploitable for many users   in the default configuration of the affected software. Examples include   serious remote denial of service of the system, local root privilege   escalations or local data theft.


[https://people.canonical.com/~ubuntu-security/priority.html](https://people.canonical.com/~ubuntu-security/priority.html)

So a strict reading of it would seem to indicate that a medium cve differs from a high cve in that it is not exploitable in the default configuration of the affected software.  Is this the way it is?  It's just the definition is pretty terse so I have my doubts it's that simple.

I looked at a few other distributions and the basic idea is that something gets in the way of the exploit such as needing action from the user or changing the default configuration.  Or the exploit is not so severe.

I've gone back to Thunderbird from the repositories as I'm no longer too worried about it but I would like to clear up this one thing since it does accumulate medium cves until the next version bump.

So what *is* a medium cve?

---

### Post by ian-weisser on 2022-12-14
The definitions seem clear and concise (not terse) to me.

And then you reiterated the same criteria that separates the two definitions in your own "*I looked at a few other distributions...*" paragraph. So you seem to understand the difference.

So yes, that's the way it is.

---

### Post by donald187 on 2022-12-14
Ok thanks!

---

### Post by donald187 on 2022-12-15
I think I can formulate my question more clearly now.  The definitions of high and medium cves don't seem to encompass all the combinations of cves there must be.  

For example, those cves that require a change in the configuration of the software or require user intervention, but might have serious consequences.  (The examples of a medium cve seem to be only those that have less serious consequences.)  And those cves that can affect software in the default configuration and don't require user intervention, but have less serious consequences.  (These don't seem to fit the first sentence in the definition of medium cve.)

Would these still be classified as medium cves?  Or what am I missing?

It's interesting to note that the definition of Low cve takes care of this problem phrasing it as low consequences or difficult to implement.

> 
Low:      Open vulnerability that is a problem but does very little damage or is   otherwise hard to exploit due to small user base or other factors such as   requiring specific environment, uncommon configuration, user assistance, etc.   These tend to be included in security updates only when higher priority   issues require an update or if many low priority issues have built up.


[https://people.canonical.com/~ubuntu-security/priority.html](https://people.canonical.com/~ubuntu-security/priority.html)

I feel that you may have already answered this but it wasn't clear to me.  Apologies if that's the case.

---

### Post by donald187 on 2022-12-15
Debian do this thing where they say a medium cve is anything that requires user interaction.  And also a few specific cases also are in the medium category.

> 
**medium** : For anything which permits code execution after user interaction.              Local privilege escalation vulnerabilities are in this category as              well, or remote privilege escalation if it's constrained to the              application (i.e., no shell access to the underlying system, such              as simple cross-site scripting). Most remote DoS vulnerabilities              fall into this category, too.


[https://security-team.debian.org/security_tracker.html#severity-levels](https://security-team.debian.org/security_tracker.html#severity-levels)

Is this the same kind of idea with Ubuntu?  I wondered if the examples in Ubuntu's definition of medium were really additional cases that are in the medium category that don't fit the real-problem, require-change-in-default-configuration criteria.

Or is the idea something like the phrasing of the low category.  Something like cves that are a real problem that require a change in the default configuration of the affected software.  Or cves whose effects are less severe.

As far as I can tell, as written the definition doesn't seem to cover all the cases as I wrote in the preceding post.

---

### Post by donald187 on 2022-12-16
So Ubuntu's definitions seem to be similar to Red Hat's definitions:

> 
Critical Impact: This rating is given to flaws that could be easily exploited by                 a remote unauthenticated attacker and lead to system compromise                 (arbitrary code execution) without requiring user interaction.                 Flaws that require authentication, local or physical access to a                 system, or an unlikely configuration are not classified as                 Critical impact. These are the types of vulnerabilities that can                 be exploited by worms.

Important Impact:  This rating is given to flaws that can easily compromise the                 confidentiality, integrity or availability of resources. These                 are the types of vulnerabilities that allow local or                 authenticated users to gain additional privileges, allow                 unauthenticated remote users to view resources that should                 otherwise be protected by authentication or other controls,                 allow authenticated remote users to execute arbitrary code, or                 allow remote users to cause a denial of service.               

Moderate Impact:  This rating is given to flaws that may be more difficult to                 exploit but could still lead to some compromise of the                 confidentiality, integrity or availability of resources under                 certain circumstances. These are the types of vulnerabilities                 that could have had a Critical or Important impact but are less                 easily exploited based on a technical evaluation of the flaw,                 and/or affect unlikely configurations. 

Low Impact:  This rating is given to all other issues that may have a                 security impact. These are the types of vulnerabilities that are                 believed to require unlikely circumstances to be able to be                 exploited, or where a successful exploit would give minimal                 consequences. This includes flaws that are present in a                 program&#8217;s source code but to which no current or theoretically                 possible, but unproven, exploitation vectors exist or were found                 during the technical analysis of the flaw.               


[https://access.redhat.com/security/updates/classification](https://access.redhat.com/security/updates/classification)

And then for convenience here are the Ubuntu cve ratings:

> 

[TABLE="class: table table-bordered table-hover key"]
[TR="class: negligible"]
[TD="class: needed"]Negligible[/TD]
[TD]   Open vulnerability that may be a problem but otherwise does not impose a   security risk due to various factors. Examples include when the vulnerability   is only theoretical in nature, requires a very special situation, has almost   no install base or does no real damage. These typically will not receive   security updates unless there is an easy fix and some other issue causes an   update.[/TD]
[/TR]
[TR="class: low"]
[TD="class: needed"]Low[/TD]
[TD]   Open vulnerability that is a problem but does very little damage or is   otherwise hard to exploit due to small user base or other factors such as   requiring specific environment, uncommon configuration, user assistance, etc.   These tend to be included in security updates only when higher priority   issues require an update or if many low priority issues have built up.[/TD]
[/TR]
[TR="class: medium"]
[TD="class: needed"]Medium[/TD]
[TD]   Open vulnerability that is a real problem and is exploitable for many users   of the affected software. Examples include network daemon denial of service,   cross-site scripting and gaining user privileges.[/TD]
[/TR]
[TR="class: high"]
[TD="class: needed"]High[/TD]
[TD]   Open vulnerability that is a real problem and is exploitable for many users   in the default configuration of the affected software. Examples include   serious remote denial of service of the system, local root privilege   escalations or local data theft.[/TD]
[/TR]
[TR="class: critical"]
[TD="class: needed"]Critical[/TD]
[TD]   Open vulnerability that is a world-burning problem and is exploitable for   most Ubuntu users. Examples include remote root privilege escalations or   remote data theft.[/TD]
[/TR]
[/TABLE]


[https://people.canonical.com/~ubuntu-security/priority.html](https://people.canonical.com/~ubuntu-security/priority.html)

The examples of high level cves in Ubuntu, namely, "serious remote denial of service of the system, local root privilege   escalations or local data theft" if they happen only on non-default configurations of the software do fit the medium definition of "a real problem". And then a cve that does little damage is categorized as low.  But it does only say that "Examples include...".  So they are not limited to such.  And I suppose the examples listed in the medium definition would be categorized as high if they are exploitable in the default configuration.  I have to admit this makes me a little uncomfortable but if the only criterion for medium versus high is default or non-default configuration than I think it has to be this way.

Anyway this seems consistent with the Ubuntu definitions.  And fits with ian-weisser's post.

---

### Post by donald187 on 2022-12-16
Or maybe "they're more like guidelines". :)

---

### Post by donald187 on 2022-12-18
> **donald187 said:**
> 
The examples of high level cves in Ubuntu, namely, "serious remote denial of service of the system, local root privilege   escalations or local data theft" if they happen only on non-default configurations of the software do fit the medium definition of "a real problem". And then a cve that does little damage is categorized as low.  But it does only say that "Examples include...".  So they are not limited to such.  And I suppose the examples listed in the medium definition would be categorized as high if they are exploitable in the default configuration.  I have to admit this makes me a little uncomfortable but if the only criterion for medium versus high is default or non-default configuration than I think it has to be this way.

But if this is the case why give the examples at all?  It doesn't make sense.

---

### Post by ian-weisser on 2022-12-18
The examples are conceptual. They are intended as an aid to understanding. If the examples detract from your understanding, then ignore the examples.

You are correct that the levels are merely guidelines to prioritize Security Team work. The levels are not intended to be a complete set of rules for categorizing CVEs fairly.

---

### Post by donald187 on 2022-12-18
I can deal with conceptual and guidelines. :)  I suppose it's just saying that medium cves tend to be less exploitable and less severe than high cves.  I guess I was wondering if I could go a step further and say that in general medium cves are either less exploitable *or* less severe (or both) than high cves. I would think that would be the case because otherwise it would tend to be a high cve (both exploitable and severe). But maybe that's a step too far and it's better to just leave it more general and recognize that it's not a fast, hard rule.

---

### Post by donald187 on 2022-12-18
Alex Murray does refer to vulnerabilities which require user input or cause smaller effects as being medium, low, or negligible so there seems to be something to this.

> 
Those which affect only a small number of users and might require  user-input or might only cause smaller effects such as a  denial-of-service may be prioritised as a medium, low or negligible.


[https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation](https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation)

I think I understand the idea well enough now.  Marking solved.  Thanks again ian-weisser!

---

### Post by donald187 on 2022-12-21
> **donald187 said:**
> 
I still wonder about the examples.  While I am ignoring them as far as classification goes I still wonder about them.  For example, if cves that are a real problem and not exploitable in the default configuration mostly tend to look like the examples in the medium definition or whether they are just as likely to look like the examples in the high definition.  Just reading it it would seem that it's the former but it seems unlikely to me that cves come neatly packed up like that but I really don't know.  But this is mild curiosity at this point and not a serious concern.

I think I'm better off not being so cause-and-effect.  If I look at it as, this is the description of a medium cve

> 
Open vulnerability that is a real problem and is exploitable for many users   of the affected software.


and this is an indication of what they look like

> 
Examples include network daemon denial of service,   cross-site scripting and gaining user privileges.


I'll be better off. Or maybe better put these are the guidelines for assigning medium cves.  The important thing for me is the fact that medium cves are not exploitable in the default configuration.  I don't have to understand everything lol.

---

### Post by donald187 on 2023-01-05
Well, I've tried to reconcile the medium definitions and examples but can't seem to do it.  As far as I can tell the medium examples have lower severity than the high examples.  (I even consulted ChatGPT lol.  Which I understand should be taken as entertainment but it brought up a couple of things I hadn't thought about.)  But if the difference between medium and high cves is that medium cves are not exploitable in the default configuration that should not mean that the medium cves are automatically less severe.  Exploitability and severity should be unrelated. One should have nothing to do with the other.  And this is what doesn't make sense to me.

Well I said before somewhere that I've gotten in trouble thinking I understood a distribution's documentation when I didn't and that's why I've asked.  ian-weisser has advised to ignore the examples so that's what I'll be doing.  (While still thinking about them from time to time. ;) )

---

### Post by ian-weisser on 2023-01-05
Well...IF the examples detract from your understanding.

Classifying CVEs as Low/Medium/High/Critical is not the goal of those definitions and examples. They are merely triage guidelines, suggesting the priorities of effort for security engineers.

They are not intended to be a complete taxonomy, and that might be one reason you seem to find them unsatisfying.

---

### Post by donald187 on 2023-01-06
I think it's simply saying that the guidelines for assigning the medium priority are that they are a real problem for many users, not exploitable in the default configuration, and have less severity than high cves.  I was thinking that the medium examples were examples of the medium definition (i.e. the first sentence) but that doesn't seem to make sense because there's nothing, I think, in the medium definition that indicates a drop in severity.  So they must just be examples of medium cves and give an idea of their severity level.  This makes sense to me.  And I understand that they are just guidelines for assigning priority of work and that cves don't fit neatly into these guidelines

---

### Post by donald187 on 2023-01-07
Thanks again ian-weisser!

---

### Post by donald187 on 2023-01-10
> **donald187 said:**
> I think it's simply saying that the guidelines for assigning the medium priority are that they are a real problem for many users, not exploitable in the default configuration, and have less severity than high cves.  I was thinking that the medium examples were examples of the medium definition (i.e. the first sentence) but that doesn't seem to make sense because there's nothing, I think, in the medium definition that indicates a drop in severity.  So they must just be examples of medium cves and give an idea of their severity level.  This makes sense to me.  And I understand that they are just guidelines for assigning priority of work and that cves don't fit neatly into these guidelines
Or at least this is my best guess.

---

### Post by donald187 on 2023-02-26
I guess the only question I have is the use of the phrase "real problem" for both high and medium cves which to me would indicate the same severity.  But the examples seem to show a drop in severity from high to medium.  The rest of the definitions have a change in terminology. For example, critical is "world-burning problem" but high is "real problem" with a corresponding drop in the severity of the examples.

Am I wrong somewhere?  Or perhaps they are not being exact with the phrase "real problem" and you're just supposed to get an idea of the severity from the examples?

---

### Post by aljames2 on 2023-02-26
As ian-weisser has pointed out, these descriptions are not strict lanes of travel that us users will know generally how every incident could be classed.  The situation at the time would earn a cve based on severity of privileges & applications affected.

I am not an expert or engineer, but as I read them, I understand medium to involve user level application exploits, and privileges.  Moving on to high, it introduces a compromise in root privileges and configurations of certain applications that would require root privileges. Any compromise of root privileges is at least of high concern.

---

### Post by donald187 on 2023-02-26
Thanks.  Just to emphasize, I'm not trying to classify every cve at this point.

---

### Post by ian-weisser on 2023-02-26
A "real problem" is defined, in each case, by a consensus of the developers and the bug-reporters.

It's similar to defining whether or not the surf at the beach is too rough for swimming. Sometimes it clearly is, sometimes it clearly isn't, sometimes there's room for persuasion.

---

### Post by donald187 on 2023-02-26
Ok thanks!

---

### Post by donald187 on 2023-03-14
Never mind.  Mods if you want to delete this go ahead.  Sorry.

---

### Post by donald187 on 2023-06-18
> **ian-weisser said:**
> The examples are conceptual. They are intended as an aid to understanding. If the examples detract from your understanding, then ignore the examples.

You are correct that the levels are merely guidelines to prioritize Security Team work. The levels are not intended to be a complete set of rules for categorizing CVEs fairly.

It sounds like the first sentence is the guideline for medium cves.  And the second sentence is to give an intuitive idea of that guideline.  Does that sound right?  So the second sentence is not meant to be a second guideline.

> 
Medium:      Open vulnerability that is a real problem and is exploitable for many  users   of the affected software. Examples include network daemon  denial of service,   cross-site scripting and gaining user privileges.


---

### Post by donald187 on 2023-06-22
> **donald187 said:**
> It sounds like the first sentence is the guideline for medium cves.  And the second sentence is to give an intuitive idea of that guideline.  Does that sound right?  So the second sentence is not meant to be a second guideline.

Hmmm.  I would have thought this was it.  It's the way I would naturally read it and it seems to fit in with your statement I previously quoted.  I tend to think that you won't say what the priorities mean because then you would be the authority and not the priorities themselves but I don't know.

So I find the cve priorities to be confusing.  With no change from high to medium except that the guidelines indicate medium cves are not vulnerable in the default configuration we get an apparent drop in "seriousness" (using a non-technical word) of the examples as far as I can tell.  So then the examples are not examples of the first sentence.

So then one might think that they are examples of medium cves in general and form a second criterion to the first sentence.  Indicating something conceptual.    But then how can I ignore them as you suggested (if I find them confusing).

So I don't get it.

---

### Post by donald187 on 2023-06-25
I think in practice the situation is similar to that in Debian.  If a cve is both not exploitable in the default configuration and one of the medium  examples then certainly it is a medium cve.  What if a cve is one of the medium examples but is exploitable in the default configuration?  Well then it would fit a medium cve under the Debian definition.

> 
**medium** : For anything which permits code execution after user interaction.              Local privilege escalation vulnerabilities are in this category as              well, or remote privilege escalation if it's constrained to the              application (i.e., no shell access to the underlying system, such              as simple cross-site scripting). Most remote DoS vulnerabilities              fall into this category, too.

[https://security-team.debian.org/security_tracker.html#severity-levels](https://security-team.debian.org/security_tracker.html#severity-levels)

There's this idea  of requiring user interaction.  But then they add in a few types of cves in addition to that.  Ubuntu must do something with these types of cves.  At worst they handle them as in Debian and label them medium.  At best they're bumped up to a high level.

Also Debian update Thunderbird on the point releases.  e.g. from 102.10.x to 102.11.0.  One time there was a release from x.y.0 to x.y.1 (I forget the actual version)  which contained some fixes for some high (according to Mozilla) cves.  Debian left it at the x.y.0 version for a month until the next point release.  (I couldn't find if it was a medium cve according to Debian.)  So they're treating the cves similarly to how Ubuntu treats it's medium cves.

So I suspect the situation in Ubuntu and Debian are rather similar.  So I'm not too worried at this point.

The quibble about the phrase "real problem" being in both the medium and high definitions is minor.

---

### Post by donald187 on 2023-06-28
> **donald187 said:**
> 
Also Debian update Thunderbird on the point releases.  e.g. from 102.10.x to 102.11.0.  One time there was a release from x.y.0 to x.y.1 (I forget the actual version)  which contained some fixes for some high (according to Mozilla) cves.  Debian left it at the x.y.0 version for a month until the next point release.  (I couldn't find if it was a medium cve according to Debian.)  So they're treating the cves similarly to how Ubuntu treats it's medium cves.

This was Thunderbird 102.3.0.  It was version-bumped on 9-27-2022 in Debian.  Mozilla released 102.3.1 a day later 9-28-2022 which fixed several high cves (according to Mozilla).  But Thunderbird wasn't version-bumped again until 10-27-2022 with 102.4.0.

[https://tracker.debian.org/pkg/thunderbird/news/?page=3](https://tracker.debian.org/pkg/thunderbird/news/?page=3)

[https://tracker.debian.org/pkg/thunderbird/news/?page=2](https://tracker.debian.org/pkg/thunderbird/news/?page=2)

[https://www.mozilla.org/en-US/security/advisories/mfsa2022-43/](https://www.mozilla.org/en-US/security/advisories/mfsa2022-43/)

---

### Post by donald187 on 2023-06-29
Of course one month sometimes to version bump Thunderbird on Debian is different than sometimes three plus months on Ubuntu.

---

### Post by QIII on 2023-06-29
You have marked this solved.  No other user has responded since February.

This thread has run its course.

Closed.

---

