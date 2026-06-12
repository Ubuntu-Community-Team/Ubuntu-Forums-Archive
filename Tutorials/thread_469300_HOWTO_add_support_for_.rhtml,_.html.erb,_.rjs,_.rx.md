---
title: "HOWTO: add support for .rhtml, .html.erb, .rjs, .rxml, .builder"
date: 2007-06-09
forum: Tutorials
---

### Post by Eric_Jardas on 2007-06-09
After you installed Ruby on Rails its time to add support for it's extensions.

**1.** First we need to add new extensions to file mime.types located in /etc folder. 

  **1.1** Lets do that. We have to add new extensions at the end of mime.types file. We'll do that with the following command:
```
echo -e "text/x-ruby-source                    rhtml html.erb \ntext/x-eruby                    rjs \napplication/xml                    rxml builder"  | sudo tee -a /etc/mime.types
```  **1.2** Now we have to update mime-types so our new extensions get loaded with:
 ```
sudo update-mime-database /usr/share/mime
```**2.** Now it's time to download [[COLOR=Blue]files.tar.gz[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=34843&stc=1&d=1181429596") from attachment

  **2.1** Unpack it with command:
```
 tar -xzvf files.tar.gz
```  **2.2** Now we have to copy .xml file to /usr/share/mime/package:
```
sudo cp x-rhtml.xml /usr/share/mime/packages
```  **2.3** And .lang files to /usr/share/gtksourceview-1.0/language-specs:
```
sudo cp *.lang /usr/share/gtksourceview-1.0/language-specs
```**And we are done ! Now editors like gedit can recognize rails extensions and you have syntax coloring for them !**

Enjoy !

---

### Post by PriceChild on 2007-06-09
talking to him on irc.

Wondering where he got this guide from... not approving yet because of the "su" start.

Please don't appove yet. If you are going to anyway, then delete this post.

---

### Post by dishkuvek on 2007-08-07
Do you know how you might get this working in gutsy?  Since in gutsy there is now gtksourceview1.0 and gtksourceview2.0, I tried putting these files in both, and I still can't get the source to highlight in gedit.

---

### Post by Brian Pattison on 2007-10-20
I can't get rhtml to be recognized in gutsy either. Can anyone please help??

---

### Post by Brian Pattison on 2007-10-20
Finally got syntax highlighting for rhtml, rjs, ect in gedit on Gutsy working!!

Hope this helps others:
[Ubuntu 7.10, rails, gedit and gtksourceview 2.0]("http://robzon.aenima.pl/2007/10/ubuntu-710-rails-gedit-and.html")

---

### Post by polypus on 2007-10-23
i have some more info for ubuntu rails gedit heads here:

[http://crepuscular-homunculus.blogspot.com/2007/10/gedit-for-ruby-and-everything-else-on.html](http://crepuscular-homunculus.blogspot.com/2007/10/gedit-for-ruby-and-everything-else-on.html)

thanks for the info!

---

### Post by Battle O'Endor on 2011-10-10
Thanks for the info.

Side note: why the **** should I register to get attached files? Is administration of this forums in desperate need of trash accounts?

---

### Post by selahlynch on 2012-02-13
I followed these instructions and was not able to get syntax highlighting for erb files working.  I'm using Ubuntu 10.04.

My ruby syntax highlighting for .rb files works fine.

---

### Post by selahlynch on 2012-02-13
x

---

### Post by selahlynch on 2012-02-13
Now I discovered that everything does indeed work properly.  My confusion stemmed from the fact that gedit saves what highlighting syntax you used last time you opened the file.  Therefor, any html.erb files that I had opened before following these instructions had saved that they should be open as plain text.  All html.erb files that I create from scratch open up with rhtml syntax highlighting.  Hooray!

---

