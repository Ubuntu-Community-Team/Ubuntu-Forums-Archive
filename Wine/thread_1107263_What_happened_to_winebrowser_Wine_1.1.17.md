---
title: "What happened to winebrowser? Wine 1.1.17"
date: 2009-03-26
forum: Wine
---

### Post by tak1150 on 2009-03-26
Hi all,

I have been using a proprietary app called SciFinder, which calls a web browser to view articles. This worked until recently after I did the trick described [here]("http://ubuntuforums.org/showthread.php?t=904621"). I was also able to troubleshoot by issuing the command:

> winebrowser [http://www.google.com](http://www.google.com)

However, the latest version of wine 1.1.17 seems to not include winebrowser. Where did it go? It seems that the structure of /home/me/.wine/drive_c/ seems very different as well. How can test to see if wine can call Firefox correctly?

Thanks!

---

### Post by SBFC on 2009-03-26
try 

```
wine iexplore
```

---

### Post by NightMKoder on 2009-03-26
Seems winebrowser moved into wine itself
```

$ wine winebrowser http://www.google.com
kfmclient(5940) ClientApp::doIt: Creating ClientApp
<unknown program name>(5942)/ ClientApp::doIt: Creating ClientApp
kioclient(5942) ClientApp::kde_open: KUrl("http://www.google.com")
kioclient(5942) KSharedUiServerProxy::KSharedUiServerProxy: kuiserver registered

```

---

### Post by tak1150 on 2009-03-27
Thanks for replying.

I guess you're right. winebrowser is still there.
So I changed the system.reg file again. I changed "...../winebrowser.exe -nohome" to "...../winebrowser.exe %1 -nohome" and it does call Firefox. However, it gives annoying error messages that I have to click on otherwise it does not let me use SciFinder :(

The one that says "DDE failure" is the first error message and if I click on it, it gives me the second one saying "cannot open...". But in fact it does open the browser.

I ran this in terminal and did not give me any error message in the terminal.

Any ideas how to fix these error messages? I know SciFinder works fine in Crossover, but it's faster in Wine and so I want to run it under Wine. Thanks!

Tak

---

### Post by trimmer on 2010-03-20
I really do not have an idea about your error message. I wish I did because this little thread solved a problem for me that I have not been able to solve until now. That whole "external weblink" issue has eluded me and I am grateful for your help!


:P:P:P:P:P:P:P:P

I would have given you 10 simleys but the forums only allow 8...

---

### Post by Zexium on 2010-03-26
I think this is what happens

If you have a DDE definition, it tries to use that, then if that fails, it falls back to the shell open command method.

Winebrowser doesn't handle the DDE properly, so you get DDE error messages and then it falls back to the command method, which works.

**Back up your registry first!**

To get round the DDE errors problem, delete the DDE key and it's subkeys, and give the HKCR\filetypename\shell\open\command key (might need to create it if a filetypename only has DDE entries) a default value of type REG_SZ with the value

"C:\windows\system32\winebrowser" %1

filetypename can be pngfile or htmlfile or http or ftp or giffile or jpegfile or mailto, I guess other values will work too such as pdffile.

I'm not sure when or why you might need to use the -nohome parameter after the %1.

Rgds

Zexium

---

