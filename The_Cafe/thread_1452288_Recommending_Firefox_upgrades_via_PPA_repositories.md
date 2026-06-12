---
title: "Recommending Firefox upgrades via PPA repositories"
date: 2010-04-11
forum: The Cafe
---

### Post by lovinglinux on 2010-04-11
I would to know the opinion of other members of the community on this subject. I have updated my Firefox tutorial today, to simplify the section [**[COLOR="Sienna"]Installing Other Versions[/COLOR]**](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1). Among the changes, I have included some notes about the use of PPA repositories and I'm stopping recommending them.

The main issues I have seen, while helping other users in the forums, are these:

[LIST]
[*]some ppa repositories like ubuntu-mozilla-daily update not only Firefox, but also other Mozilla applications, like Thunderbird. Several users using this method are not aware of this and struggle to downgrade other Mozilla applications.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, several users don&#8217;t know the difference, so the forums end up with countless threads complaining why the browser is called Shiretoko or Namoroka.
[*]some repositories like mozillateam/firefox-stable doesn&#8217;t seem to be updated frequently, thus missing important security patches.
[*]some repositories like ubuntu-mozilla-daily upgrade Firefox with unstable releases, sometimes causing serious issues, like crashing the browser when viewing flash content. Additionally, several users don&#8217;t realize they got an unstable version of Firefox because of the ppa updating policy.
[/LIST]

I have been thinking lately about the pros and cons of widespread recommendation of ppa repositories for Firefox, specially those that doesn't explain potential issues. This week several threads being posted seems to be related to an ubuntu-mozilla-daily bug, that causes flash to crash the browser. It seems this problem is ironically related to new Lorentz technology that prevents plugins from crashing the browser.

BTW, if you download the latest [Lorentz](http://www.mozilla.com/en-US/firefox/lorentz/) from Mozilla this problem does not occur and the browser doesn't crash or lock, even if you browse a messed up flash video. Is a very nice technology.

So what do you think about the recommendation of ppa repositories for Firefox upgrade? Do you think that downloading Firefox from Mozilla and simply extracting it to the user home directory is a safer option?

---

