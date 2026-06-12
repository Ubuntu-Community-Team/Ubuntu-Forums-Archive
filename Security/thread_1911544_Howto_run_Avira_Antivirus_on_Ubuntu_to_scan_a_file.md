---
title: "Howto run Avira Antivirus on Ubuntu to scan a file or directory"
date: 2012-01-19
forum: Security
---

### Post by soresger on 2012-01-19
I installed the free version of Avira Antivirus onto my Ubuntu system but I wasn't able to install Dazuko.

I want to learn how to scan a file or directory. 

If somebody could please help, it will be appreciated.

---

### Post by Ms. Daisy on 2012-01-20
Have you tried the Avira website? They would probably have the best information on how to run their tool.

---

### Post by SeijiSensei on 2012-01-20
Use [ClamAV]("http://www.clamav.net/").  It's free and supported in the Ubuntu repositories.

```

sudo apt-get install clamav 
sudo freshclam
clamscan /path/to/your/file

```

freshclam updates the virus signature library.  You might see errors about your version being out of date.  Don't worry about that; just scan your file(s).

You can scan whole directories.  If you have a Windows partition mounted in Linux you can run clamscan on the Linux side to scan all your Windows files.

---

