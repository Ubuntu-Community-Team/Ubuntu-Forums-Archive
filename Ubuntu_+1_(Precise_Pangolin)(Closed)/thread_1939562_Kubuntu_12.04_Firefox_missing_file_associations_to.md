---
title: "Kubuntu 12.04 Firefox missing file associations to open downloads"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MountainX on 2012-03-11
I just installed Kubuntu 12.04 beta 1. 

Both Rekong and Firefox don't know how to "Open Containing Folder" of downloaded items or open the item itself. 

Rekong is installed by default and the problem is present in a standard configuration.

To reproduce, download a file with Rekong. Then go to downloads > Open directory (of the downloaded file). The result is:
Error: rekonq does not know how to handle this protocol: 

The same situation exists in Firefox. I used the included Kubuntu menu item to install Firefox. No problems with the installation.

But when I download an item (e.g., a JPG image) with Firefox and then choose to either open it or open the containing folder, I get a dialog titled "launch application" and I have to "choose an application". 

_More Info_

In Firefox preferences > Applications, the only content types shown are irc, ircs, mailto, podcast, tar file, webca and webfeed. Normally, there would be many more. 

I tried deleting mimeTypes.rdf (as mentioned in a Mozilla Knowledge Base article) in my Firefox profile and it did not resolve the issue.

I also tried copying a known good working Firefox profile from my other computer. Once I began using that profile, it also had the problem. It looks like a Kubuntu issue, not a Firefox or Rekong issue.

Here's some more info:
```

    $ cat ~/.local/share/applications/mimeapps.list  
    cat: /home/user/.local/share/applications/mimeapps.list: No such file or directory

    $ cat /usr/share/applications/defaults.list  
    cat: /usr/share/applications/defaults.list: No such file or directory

```Unfortunately, copying those files from a working Ubuntu installation did not resolve the issue.

The default applications for handling files in Dolphin works correctly.

If I tell Firefox to remember the file associations, that creates a new problem. Every file opens in Dolphin first, then Dolphin opens the correct applicaation. 

There's a similar question [here][1] with no solution.

  [1]: [http://askubuntu.com/questions/51008/web-browser-downloads-only-open-target-folders-cannot-open-files](http://askubuntu.com/questions/51008/web-browser-downloads-only-open-target-folders-cannot-open-files)

Here's a question where the person had a similar problem but it was both caused and solved by entirely different things from my situation:
[http://askubuntu.com/questions/51008/web-browser-downloads-only-open-target-folders-cannot-open-files](http://askubuntu.com/questions/51008/web-browser-downloads-only-open-target-folders-cannot-open-files)

---

### Post by MountainX on 2012-04-06
I posed the solution here:
[http://askubuntu.com/questions/112194/kubuntu-12-04-firefox-and-rekong-dont-know-how-to-open-downloaded-files](http://askubuntu.com/questions/112194/kubuntu-12-04-firefox-and-rekong-dont-know-how-to-open-downloaded-files)

---

