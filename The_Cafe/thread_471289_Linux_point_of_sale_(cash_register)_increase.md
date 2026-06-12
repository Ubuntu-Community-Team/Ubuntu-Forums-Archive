---
title: "Linux point of sale (cash register) increase?"
date: 2007-06-11
forum: The Cafe
---

### Post by earobinson on 2007-06-11
I have been seeing in the number of cash registers that seem to be running linux lately, anyone know what software these are running?

Google seems to have failed me.

---

### Post by smoker on 2007-06-11
these may be useful to you:
[http://www.computerwire.com/industries/research/?pid=FDFEB9DD-055A-425E-A2AF-DBE94137EDF5](http://www.computerwire.com/industries/research/?pid=FDFEB9DD-055A-425E-A2AF-DBE94137EDF5)

[http://linux.omnipotent.net/article.php?article_id=9958](http://linux.omnipotent.net/article.php?article_id=9958)

---

### Post by JAPrufrock on 2007-06-12
> **earobinson said:**
> I have been seeing in the number of cash registers that seem to be running linux lately, anyone know what software these are running?

Google seems to have failed me.

Not having an open source point of sale is the main reason why open source Linux distros like Ubuntu are not being used in small businesses.  I have been desparately looking for open source point of sale software with little luck.  Gnucash is a nice little open source accounting program that can use multiple currencies, but doesn't include a point of sale. I did find one Web based point of sale called PHP Point of Sale.  It uses PHP and MySQL and has a GPL.  It's Web based, though, which is not the ideal situation.

---

### Post by earobinson on 2007-06-12
> **JAPrufrock said:**
> Not having an open source point of sale is the main reason why open source Linux distros like Ubuntu are not being used in small businesses.  I have been desparately looking for open source point of sale software with little luck.  Gnucash is a nice little open source accounting program that can use multiple currencies, but doesn't include a point of sale. I did find one Web based point of sale called PHP Point of Sale.  It uses PHP and MySQL and has a GPL.  It's Web based, though, which is not the ideal situation.
Why isent web based any good?

---

### Post by mips on 2007-06-12
Linux is pretty big in POS. I actually did some research about 18months ago and was kinda amazed. We even have a local company developing their own POS stuff that runs on Linux.

---

### Post by jgrabham on 2007-06-12
Tesco do!!

---

### Post by DigitalDuality on 2007-06-12
d

---

### Post by earobinson on 2007-06-12
> **mips said:**
> Linux is pretty big in POS. I actually did some research about 18months ago and was kinda amazed. We even have a local company developing their own POS stuff that runs on Linux.
any idea what the name of the programs they use are, and the OS?

---

### Post by mips on 2007-06-12
> **earobinson said:**
> any idea what the name of the programs they use are, and the OS?

I will have a look for you. If you have not heard from me in 2 days PM me as I'm a bit on the forgetfull side.

Edit:
Keep [http://www.cubit.co.za/index.php](http://www.cubit.co.za/index.php) in mind, i think they have a POS module.

Let me carry on with the searching.

---

### Post by earobinson on 2007-06-12
I have been doing a bit of searching to, I know that there are a lot of close source ones for red hat but thats all I have found, maybe a ubuntu POS project could be part of the future.

Anyone whoe wants to brainstorm what features are needed in a POS system feel free to post them here!

---

### Post by mips on 2007-06-12
> **earobinson said:**
> I have been doing a bit of searching to, I know that there are a lot of close source ones for red hat but thats all I have found, maybe a ubuntu POS project could be part of the future.

Anyone whoe wants to brainstorm what features are needed in a POS system feel free to post them here!

Google GPL POS

All these are GPL but not always linux, nothing stops you from porting though:

[http://sourceforge.net/projects/freemercator/](http://sourceforge.net/projects/freemercator/)
[http://tinapos.sourceforge.net/](http://tinapos.sourceforge.net/)
[http://www.bananahead.com/pos/home.html](http://www.bananahead.com/pos/home.html)
[http://www.viewtouch.com/](http://www.viewtouch.com/)
[http://easypos.sourceforge.net/](http://easypos.sourceforge.net/)
[http://www.phppointofsale.com/](http://www.phppointofsale.com/)
[http://sourceforge.net/projects/l-ane/](http://sourceforge.net/projects/l-ane/)
[http://d-pos.usefulz.com/](http://d-pos.usefulz.com/)
[http://www.dolesoft.com/](http://www.dolesoft.com/)

---

### Post by earobinson on 2007-06-13
Thanks for the links, I assume this means there is currently no linux project.

---

### Post by auburn on 2007-06-13
We use TinaPOS at my job which is java-based and supports touch screens: [http://tinapos.sourceforge.net/](http://tinapos.sourceforge.net/)

---

### Post by earobinson on 2007-06-13
> **auburn said:**
> We use TinaPOS at my job which is java-based and supports touch screens: [http://tinapos.sourceforge.net/](http://tinapos.sourceforge.net/)
Ya thats the first one I looked at but I seem to be getting all sorts of errors > $ ./tinapos.sh 
Header Chunk. Image width:32 height:32 depth:8 color type:6 compression type:0 filter type:0 interlace:0
Header Chunk. Image width:32 height:32 depth:8 color type:6 compression type:0 filter type:0 interlace:0
align: javax.swing.text.html.BlockView@203c80
align: javax.swing.text.html.InlineView@dca50
align: javax.swing.text.html.BRView@429948
align: javax.swing.text.html.InlineView@dca20
align: javax.swing.text.html.BRView@429918
align: javax.swing.text.html.InlineView@dc9f0
align: javax.swing.text.html.BRView@4298e8
align: javax.swing.text.html.InlineView@dc9c0
align: javax.swing.text.html.BRView@4298b8
align: javax.swing.text.html.BRView@4298a0
align: javax.swing.text.html.BRView@429870
align: javax.swing.text.html.BRView@429858
align: javax.swing.text.html.InlineView@dc960
align: javax.swing.text.html.BRView@429828
align: javax.swing.text.html.BRView@429810
align: javax.swing.text.html.InlineView@dc930
align: javax.swing.text.html.BRView@4297e0
Header Chunk. Image width:32 height:32 depth:8 color type:6 compression type:0 filter type:0 interlace:0
Exception during event dispatch:
java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.70)
   at net.adrianromero.tpv.ticket.TaxInfo.toString(Unknown Source)
   at javax.swing.plaf.basic.BasicComboBoxEditor.setItem(libgcj.so.70)
   at javax.swing.JComboBox.configureEditor(libgcj.so.70)
   at javax.swing.plaf.basic.BasicComboBoxUI$ItemHandler.itemStateChanged(libgcj.so.70)
   at javax.swing.JComboBox.fireItemStateChanged(libgcj.so.70)
   at javax.swing.JComboBox.selectedItemChanged(libgcj.so.70)
   at javax.swing.JComboBox.contentsChanged(libgcj.so.70)
   at javax.swing.AbstractListModel.fireContentsChanged(libgcj.so.70)
   at net.adrianromero.data.gui.ComboBoxValModel.setSelectedItem(Unknown Source)
   at javax.swing.JComboBox.setSelectedItem(libgcj.so.70)
   at javax.swing.JComboBox.setSelectedIndex(libgcj.so.70)
   at javax.swing.plaf.basic.BasicComboPopup$PropertyChangeHandler.propertyChange(libgcj.so.70)
   at java.beans.PropertyChangeSupport.firePropertyChange(libgcj.so.70)
   at java.beans.PropertyChangeSupport.firePropertyChange(libgcj.so.70)
   at java.awt.Component.firePropertyChange(libgcj.so.70)
   at javax.swing.JComboBox.setModel(libgcj.so.70)
   at net.adrianromero.tpv.panelsales.JPanelTicket.activate(Unknown Source)
   at net.adrianromero.tpv.panelsales.JPanelTicketSales.activate(Unknown Source)
   at net.adrianromero.tpv.forms.JPrincipalApp.showTask(Unknown Source)
   at net.adrianromero.tpv.forms.JPrincipalApp$PanelAction.actionPerformed(Unknown Source)
   at net.adrianromero.tpv.forms.JPrincipalApp.<init>(Unknown Source)
   at net.adrianromero.tpv.forms.JFrmTPV.openAppView(Unknown Source)
   at net.adrianromero.tpv.forms.JFrmTPV.access$200(Unknown Source)
   at net.adrianromero.tpv.forms.JFrmTPV$AppUserAction.actionPerformed(Unknown Source)
   at javax.swing.AbstractButton.fireActionPerformed(libgcj.so.70)
   at javax.swing.AbstractButton$1.actionPerformed(libgcj.so.70)
   at javax.swing.DefaultButtonModel.fireActionPerformed(libgcj.so.70)
   at javax.swing.DefaultButtonModel.setPressed(libgcj.so.70)
   at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(libgcj.so.70)
   at java.awt.Component.processMouseEvent(libgcj.so.70)
   at java.awt.Component.processEvent(libgcj.so.70)
   at java.awt.Container.processEvent(libgcj.so.70)
   at java.awt.Component.dispatchEventImpl(libgcj.so.70)
   at java.awt.Container.dispatchEventImpl(libgcj.so.70)
   at java.awt.Component.dispatchEvent(libgcj.so.70)
   at java.awt.LightweightDispatcher.handleMouseEvent(libgcj.so.70)
   at java.awt.LightweightDispatcher.dispatchEvent(libgcj.so.70)
   at java.awt.Container.dispatchEventImpl(libgcj.so.70)
   at java.awt.Window.dispatchEventImpl(libgcj.so.70)
   at java.awt.Component.dispatchEvent(libgcj.so.70)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.70)
   at java.awt.EventDispatchThread.run(libgcj.so.70)
Caused by: java.lang.IllegalArgumentException: The currency code, $, is not supported.
   at java.util.Currency.getInstance(libgcj.so.70)
   at java.text.DecimalFormatSymbols.getCurrency(libgcj.so.70)
   at java.text.DecimalFormat.getCurrency(libgcj.so.70)
   at java.text.NumberFormat.getCurrencyInstance(libgcj.so.70)
   at java.text.NumberFormat.getCurrencyInstance(libgcj.so.70)
   at net.adrianromero.format.Formats.<clinit>(Unknown Source)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...42 more

If you have any idea how to fix them I would be happy to try

---

### Post by mips on 2007-06-13
> **earobinson said:**
> I assume this means there is currently no linux project.

Some of those are linux.

---

### Post by JAPrufrock on 2007-06-13
> **earobinson said:**
> Why isent web based any good?

When I responded to this thread, I forgot to mention that I was looking for a open source POS that would also work in Spanish.  Since Gnucash has multilanguange functionability, a multilanguage POS that could be used in coordination with Gnucash would be incredibly useful in the non-English speaking world.  The only free (as in beer) and free (as in open source) multilanguage POS that I could find was PHP Point of Sale.  I haven't compiled it yet, but the program runs in a browser, like Firefox, and so I'm assuming that it has to be used online.  Since I don't have a great internet connection where I live, it may not be suitable for my needs.

---

### Post by auburn on 2007-06-16
tinapos is in spanish too. [http://tinapos.sourceforge.net/index_es.php](http://tinapos.sourceforge.net/index_es.php)
The developer is from Spain or Portugal.

I don't think those are errors you listed. That's simply tinapos loading. But tinapos (the way it's supposed to be run) requires setting up with a database eg mysql. But you should be able to try it out with the temporary HSQLDB database it comes with.

Here's the wikibooks on how to install it:
[http://en.wikibooks.org/wiki/Using_Tina_POS/Installation_guide](http://en.wikibooks.org/wiki/Using_Tina_POS/Installation_guide)

Btw, I haven't found it *so* flexible with haphazardly chosen hardware. Generally the developer just recommends you buy some of the cash drawer/printer combos he's tested on. (A good idea anyway).

tinapos forums:
[http://sourceforge.net/forum/?group_id=127939](http://sourceforge.net/forum/?group_id=127939)

---

### Post by auburn on 2007-06-16
oh, I know. You needed to run ```
./configure.sh
``` before you ran ```
tinapos.sh
```. Did you do that?

---

### Post by earobinson on 2007-06-16
> **auburn said:**
> oh, I know. You needed to run ```
./configure.sh
``` before you ran ```
tinapos.sh
```. Did you do that?
ya i did :(

---

### Post by auburn on 2007-06-22
I seem to not be paying much attention to this forum, but I've gotten great results searching the tinapos forums on sourceforge. Adrian (the developer) will respond to lot of the queries himself. I would look into making sure your java dependencies are met and you fill out the configuration screen correctly. I really think tinapos is the best looking pos out there. I guess it does require a little tinkering to get the whole database set up correctly.

---

### Post by wallcrawler78 on 2007-06-25
For a Spanish based POS system you might look at NTPV it is pretty cool  There is also a forum for it online.. but i will have to find the link.  I have about 5 yrs POS experience and would love to create a solution.  I have started creating menus and the such in QT but dont really have any skill in the actual programing... if someone was interested in helping out though i would love to work twords making something really powerful for Ubuntu.

My plans are to start off with counter service (easiest), then Bar (hickup..), then move into Fine dinining...  Fine dinning is the hardest since there is soooo much to worry about.  coursing,  preptimes, etc...

Anyone who is willing to work with me on this... let me know! I have experience deploying mulitple POS solutions (digital dinning, Aloha, remanco, RMS touch) and have worked with over 300 resturants.... when it comes to how it should function, i have the knowlege to be useful... when it comes to creating code... pretty useless.


Daniel

---

### Post by daller on 2007-07-17
I've been testing PHP Point of Sale, and it seems quite nice!

Nothing keeps your from installing MySQL and PHP, and run it locally!

---

