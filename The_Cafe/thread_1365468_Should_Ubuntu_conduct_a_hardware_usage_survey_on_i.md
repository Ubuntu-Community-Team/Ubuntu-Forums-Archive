---
title: "Should Ubuntu conduct a hardware usage survey on it's users?"
date: 2009-12-27
forum: The Cafe
---

### Post by diablo75 on 2009-12-27
If you've ever played video games on Windows (or Ubuntu via WINE) through Steam, you've probably gotten a "Would you like to participate in a brief annonymous survey to help improve Steam?"

I've always liked doing these surveys because they take less than 30 seconds and the stats that are published online after all the digits are aggrigated are pretty neat to look at.

I was thinking it would be benificial to the community if a small app were developed to gather general information about hardware usage to help generate similar statistical output for the community to look at but with an opportunity for the person taking the survey to include additional comments about specific hardware they're using if they wish.  All this information would be stored in an online database.  The comments could then be compiled and accessible to others through the same app to see what others have said about the same hardware they are also using.  So for example, if I took a survey and left a comment specifically about the fingerprint scanner on my laptop, "I took these steps to get the fingerprint scanner working properly," someone else who has that exact same scanner in their laptop could see what I typed about that piece of hardware and even get their hardware running without having to consult the forums or google.  All they would have to do is run a little utility that would scan their system and give them instant access to a live database that is populated with device specific stats and community comments.

Another potential use for this could be for people who aren't even running Ubuntu yet to download an easy to use "Hardware Compatabilty Check" utility that will scan their hardware and tell them whether or not they should anticipate specific issues.  Something like this existed back before Windows XP came out which would let people know if their computer was ready for an upgrade or if there were still issues out there.  The same kind of benifit could be used to help prempt the kind of, "I upgraded and now this and that doesn't work anymore" problems that seem to happen all the time.

Does something like this already exist?  If it doesn't, I'd gladly submit it to Brainstorm as an idea.  If it does exist, I think it really should be made a default app in the distro so people are asked after a week or two of usage if they'd like to become involved with this sort of thing.

---

### Post by Psumi on 2009-12-27
System > Administration > System Testing

The package/application (for those of you who do minimal ubuntu installs) is called checkbox and checkbox-gtk.

You can check your own hardware/testing submissions that are sent to launchpad by going here:
```
https://launchpad.net/~[username]/+hwdb-submissions
```

---

### Post by diablo75 on 2009-12-27
> **Psumi said:**
> System > Administration > System Testing

The package/application (for those of you who do minimal ubuntu installs) is called checkbox and checkbox-gtk.

You can check your own hardware/testing submissions that are sent to launchpad by going here:
```
https://launchpad.net/~[username]/+hwdb-submissions
```

I submitted a hardware profile and checked out the link above.  I'm not sure how to use the information that was submitted.  It's a table, divided into System, Date Submitted, Download, Private and Raw.  The "System" column has a link with a bunch of numbers and letters, and after clicking on it, I'm taking to a page that has a list of "Hardware submissions for a fingerprint" and what appears to be a list of over 100,000 other surveys that have been submitted by other people with the same finger print.  So if I were to take a totally uneducated guess, this means over 100,000 people have done tests using the exact same laptop as me with their results typed up in a XML file and archived in a bz2.  Is that correct?

Another question I had in the OP was if a database like this could be used to help Ubuntu-curious users run a hardware compatibility check on their system with a little utility that would compare their hardware to the database.  Does something like this exist?

---

### Post by Psumi on 2009-12-27
> **diablo75 said:**
> Another question I had in the OP was if a database like this could be used to help Ubuntu-curious users run a hardware compatibility check on their system with a little utility that would compare their hardware to the database.  Does something like this exist?

A better web interface is planned: [https://answers.launchpad.net/checkbox/+question/26749](https://answers.launchpad.net/checkbox/+question/26749)

But when it will come out, we don't know.

---

### Post by Frak on 2009-12-27
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by 23meg on 2009-12-27
> **Frak said:**
> [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

To avoid a possible misunderstanding: that website doesn't have anything to do with data produced by Checkbox.

---

