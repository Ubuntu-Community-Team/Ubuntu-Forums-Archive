---
title: "Is this possible? Launching one Wine program from another"
date: 2009-06-23
forum: Wine
---

### Post by Nugar on 2009-06-23
Hi all,

Recently, I got Photoshop CS4 working under Wine 1.1.24. It was portable version.

Also, I use BreezeBrowser Pro to manage my photos. Under Windows, I can set up Photoshop as my editor for BreezeBrowser, just let the program know the path and you're ready.

Is this possible under wine? I've tried: 

wine "/path/to/pscs4/Photoshop.exe"

wine \"/path/to/pscs4/Photoshop.exe\"

to no avail.

Is this possible at all?

Thanks in advance,

Nugar

---

### Post by rocky5051 on 2009-06-23
I couldn't see why not. The Windows version of Firefox, under Wine, can initiate other Windows applications you've downloaded from within it's download manager if you choose to do so.

I would assume the path you give CS4 would be in terms of the virtual C:\ drive, assuming you let Wine install BreezeBrowser to this directory.

You wouldn't need to include the wine command for it to do it, I believe.

---

### Post by Nugar on 2009-06-23
Thanks, Rocky.  It doesn't work, I'm sorry to say.

---

### Post by NightMKoder on 2009-06-23
If you're specifying an application to launch from within a windows app - you need to specify it in windows terms. ie.

wine "/path/to/pscs4/Photoshop.exe"

becomes

"C:\Program Files\...\Photoshop.exe"

---

### Post by Nugar on 2009-06-24
Thanks NightMKoder. In this particular case it doesn't work.

Cheers,

Nugar

---

### Post by cogadh on 2009-06-24
Define "it doesn't work". What exactly happens when you do that? Is there any error output from the app or Wine?

---

### Post by Nugar on 2009-06-24
Hello cogadh,

Thanks for your post.

The way it is supposed to work is this:

[LIST]
[*]I add the path to Photoshop to the BreezeBrowser preferences as the default external editor.
[*]Once added, I can right-click on an image and select "edit" and Photoshop should open and in turn open the image (in my case, it opens in Adobe Camera Raw, actually)
[/LIST]
That second step is not working. Photoshop won't open.

There are no error messages, neither from Wine, Breezebrowser nor PS. PS just won't open.

But I can live with that. Making that work would make my life easier, but not a deal-breaker.

Thanks again,

Nugar

---

### Post by NightMKoder on 2009-06-24
Can you post a wine log from trying to open it?

---

### Post by Nugar on 2009-06-25
Hmmm... I don't know how to do that!

---

### Post by cogadh on 2009-06-25
Run the app via the terminal, Wine will output its own error messages there. For example:
```
cd ~/.wine/drive_c/Program\ Files/path/to/app
wine app.exe
```
When you try to launch PS from BreezeBrowser, Wine should produce some kind of informative message in the terminal.

---

### Post by Nugar on 2009-06-25
This is what I get:

```
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!

```

---

