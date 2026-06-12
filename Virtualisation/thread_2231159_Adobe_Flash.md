---
title: "Adobe Flash"
date: 2014-06-23
forum: Virtualisation
---

### Post by kakashi_12 on 2014-06-23
I'm finding that Adobe Flash will only go up to version 11.2 for Linux.
For Windows Adobe Flash is up to version 14.
There is a side note on Adobe's site that said they won't upgrade Flash any more than that for Linux.

Before I go installing a virtual machine of XP on here, can anyone tell me if an install of IE through Wine would work and also an install of flash plug-in through Wine would work? Anyone test this before??? Any other ideas?

Thanks.

---

### Post by maestrobwh1 on 2014-06-23
IE via Wine was never all that stable, and with flash, I just can't imagine that would be the way to go.  Last I was ever able to have IE running in wine, it was version 6 and IE only sort of worked.  You "might" be able to get one of the other browsers to work under wine with flash.

---

### Post by SeijiSensei on 2014-06-23
Take a look at [pipelight]("http://pipelight.net/cms/installation.html").  It installs a customized version of WINE that supports Silverlight and the Windows version of Flash player.  Easy installation instructions are [here]("http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html").  

That said, I found using the Windows version was a bit buggy when going into and out of full screen.  I reverted back to the Linux version.  There's nothing I want to watch in Flash that doesn't work with the Linux player.

---

### Post by kakashi_12 on 2014-06-23
hmmmm. what do you mean exactly? how?

---

### Post by kurt18947 on 2014-06-23
Do you run anything that doesn't work with Flash 11.2.whatever?  I've not seen an issue but then I don't do anything flash related except watch videos.  Adobe is supporting 11.2.xxx in linux with security updates until around 2017 if I recall correctly.  If you must have the latest flash version, you could install Chrome which comes with the latest flash version already installed or Chromium.  With Chromium you'd need to install pepper-flash which is in the repositories.  I did that just to see if it would work, Chromium played videos fine but I saw no difference between Firefox with Flash 11.2.xxx and Chromium with pepper-flash.

---

### Post by kakashi_12 on 2014-06-23
User plays facebook games. Only some work. Some get message saying needs flash updated.
Already tried chrome, but not pepper flash. I'll try that. Thanks!

---

### Post by deadflowr on 2014-06-23
> **kakashi_12 said:**
> User plays facebook games. Only some work. Some get message saying needs flash updated.
Already tried chrome, but not pepper flash. I'll try that. Thanks!

?
pepperflash is built into chrome.
If you've used chrome, unless you disabled it, you've used it.

(*&#8203; I refer to chrome and not chromium)*

---

### Post by kakashi_12 on 2014-06-23
Is there a difference between chrome and chromium? Im guessing not.
Repositories? Can I get to that from Software Center?

---

### Post by kakashi_12 on 2014-06-24
?

---

### Post by SeijiSensei on 2014-06-24
> **kakashi_12 said:**
> hmmmm. what do you mean exactly? how?

Did you read the two linked documents in my reply?  They spell it all out for you.

---

### Post by kakashi_12 on 2014-06-25
PipeLight. Sorry, didn't see that. I guess I overread it. My bad. Let me give that a try. Thanks.

---

### Post by kakashi_12 on 2014-06-25
I'm stuck on the 3rd command
sudo apt-get install --install-recommends pipelight-multi
 After it runs, I can't click Ok to go back to Terminal. (see attachment)
I can exit terminal and open a new one. But not sure if that will screw up installation or not.

---

### Post by SeijiSensei on 2014-06-25
Does the command finish and leave you back at the command prompt?  If so, it has finished the installation.

---

### Post by kakashi_12 on 2014-06-25
It does not bring me back to the terminal. I can hold in ESC and it will flash and show me the terminal screen behind it, but will not exit. 
Clicking Ok does nothing and holding enter does nothing except go down the UELA.

I opened a new Terminal and tried to proceed to the next command in the next step. It would not continue.

---

### Post by kurt18947 on 2014-06-25
> **kakashi_12 said:**
> Is there a difference between chrome and chromium? Im guessing not.
Repositories? Can I get to that from Software Center?

One of the differences between Chrome and Chromium is that Chrome comes with pepper-flash already installed. Chromium excludes proprietary bits like pepper-flash and a pdf reader.  I installed pepper-flash from Ubuntu's repository.

---

### Post by SeijiSensei on 2014-06-25
> **kakashi_12 said:**
> Clicking Ok does nothing and holding enter does nothing except go down the UELA.

If you mean clicking with the mouse, that won't work in a terminal.  It expects all the input to come from the keyboard.

When you see the EULA screen, you need to use the Tab to navigate to OK and hit Enter.

---

### Post by kakashi_12 on 2014-06-25
I didn't think "clicking" would work. But I had no other alternative 'cause no key strokes were working. Enter and Ctrl C or anything. Thanks, I'll keep that in mind for next time... to use Tab.

 Although, I tried Kurt's idea instead (seemed a lot easier). Chrome (instead of Chromium) installed. Did a search for Chrome and went to their website, downloaded the 32 bit DEB file. Then had it open and install through Software Center.
 Opened. It tells me I have version 14 of flash. Which is great, plus it also says it auto updates!
 Now I just have to have the 'user' test it on their pc since they are the one that actually plays the games :)

---

### Post by deadflowr on 2014-06-27
> **kakashi_12 said:**
> Is there a difference between chrome and chromium? Im guessing not.
Repositories? Can I get to that from Software Center?

Late reply, but yes. There is a difference between chrome and chromium.
Chromium is a community-built browser.
Google funds the chromium project, but then takes the core parts and adds it's own pieces, which make up chrome.
Most notable is that chrome has flash built-in, and chromium does not.

chromium is open-source and available in the default Ubuntu repositories.
chrome is not and to install you either need to install the deb package from google-chrome, or add the google-chrome repository and then install via apt-get.

---

