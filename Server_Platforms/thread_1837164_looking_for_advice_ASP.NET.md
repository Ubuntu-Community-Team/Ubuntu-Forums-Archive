---
title: "looking for advice ASP.NET"
date: 2011-09-01
forum: Server Platforms
---

### Post by Drenriza on 2011-09-01
Hi all.

I have created a small website with ASP.NET and installed a Ubuntu 10.04LTS server with apache2, mono and xsp2. Now i wanted to upload my website from my local machine to the server. But what files do i need to upload and place in the /var/www/ folder?

These are my files
ArrayManagement.cs,		Locatel.csproj.user,	Web.Debug.config,		WebForm1.aspx,			bin,
GetAndSetMethodes.cs,		Methodes.cs,			Web.Release.config,		WebForm1.aspx.cs,		obj,
Locatel.csproj,		Properties,			Web.config,			WebForm1.aspx.designer.cs,

Also i guess i need to compile the C# code before i can use it, as code-behind.

Kind regards.

EDIT:
If i upload the WebForm1.aspx to the /var/www/ folder on my server. And http to the address. It gives me the option to download the file, but it docent display the actual webpage. Is it me who are wrong here?

---

### Post by directhex on 2011-09-01
> **Drenriza said:**
> Hi all.

I have created a small website with ASP.NET and installed a Ubuntu 10.04LTS server with apache2, mono and xsp2. Now i wanted to upload my website from my local machine to the server. But what files do i need to upload and place in the /var/www/ folder?

These are my files
ArrayManagement.cs,		Locatel.csproj.user,	Web.Debug.config,		WebForm1.aspx,			bin,
GetAndSetMethodes.cs,		Methodes.cs,			Web.Release.config,		WebForm1.aspx.cs,		obj,
Locatel.csproj,		Properties,			Web.config,			WebForm1.aspx.designer.cs,

Also i guess i need to compile the C# code before i can use it, as code-behind.

Kind regards.

EDIT:
If i upload the WebForm1.aspx to the /var/www/ folder on my server. And http to the address. It gives me the option to download the file, but it docent display the actual webpage. Is it me who are wrong here?

Did you configure Apache properly? e.g. did you enable mod-mono? If you just want to blindly process content from /var/www, you should run "a2enmod mod_mono_auto" then restart Apache

---

### Post by Drenriza on 2011-09-01
> **directhex said:**
> Did you configure Apache properly? e.g. did you enable mod-mono? If you just want to blindly process content from /var/www, you should run "a2enmod mod_mono_auto" then restart Apache

Their is of course a possibility that apache has been configured wrongly. What configurations for my "issue" would you suggest? Or do you have a place where i can go and read about configuring apache2 for asp.net services. I haven't found any good places, as of now. I have enabled a2enmod mod_mono_auto and it did not make a change.

When i go to the address that the apache service runs on. I get an index of what lies in the /var/www/ folder. Here i can click on my WebForm1.aspx where i then get an error.

Its a learning process. All advice and suggestions are welcome.

---

### Post by directhex on 2011-09-01
> **Drenriza said:**
> I have enabled a2enmod mod_mono_auto and it did not make a change

Yes it did. In your original post, you said Apache was downloading aspx files rather than rendering them. Now it's trying to render them.

> When i go to the address that the apache service runs on. I get an index of what lies in the /var/www/ folder.

That's normal. If you visit an URL, you get a directory listing unless there's a file with one of the default filenames in that folder (e.g. index.html is a common default filename, so [http://foo.com](http://foo.com) will load the file index.html rather than offering a directory listing).

> Here i can click on my WebForm1.aspx where i then get an error.

Do you have error reporting disabled in your web.config? That makes it rather hard to debug.

---

### Post by Drenriza on 2011-09-02
Is their a place where you can read on how to deploy a asp.net website on ubuntu, and configuring xsp2 to listen to /var/www/ instead of /home/username/

And what is necessary on the server side to make this work, its quite annoying.

---

### Post by directhex on 2011-09-02
> **Drenriza said:**
> Is their a place where you can read on how to deploy a asp.net website on ubuntu, and configuring xsp2 to listen to /var/www/ instead of /home/username/

So you want to use XSP2 as a standalone ASP.NET 2.0 server? I thought you wanted to use Apache as a frontend?

> And what is necessary on the server side to make this work, its quite annoying.

A detailed explanation of what "this" and "work" are in context. Since all the software works fine with a valid configuration.

---

### Post by Drenriza on 2011-09-03
> **directhex said:**
> So you want to use XSP2 as a standalone ASP.NET 2.0 server? I thought you wanted to use Apache as a frontend?

Im just trying to find something that works. All the guides i can find uses mono-xsp as their server for ASP.NET. Im trying to figure out what to use, since their are no decent guides on the subject. That i have been able to find. Only bits and pieces.

---

### Post by directhex on 2011-09-04
> **Drenriza said:**
> Im just trying to find something that works. All the guides i can find uses mono-xsp as their server for ASP.NET. Im trying to figure out what to use, since their are no decent guides on the subject. That i have been able to find. Only bits and pieces.

Just to check... Did you actually read the readme files in the packages you installed? The ones in /usr/share/doc/ ?

---

