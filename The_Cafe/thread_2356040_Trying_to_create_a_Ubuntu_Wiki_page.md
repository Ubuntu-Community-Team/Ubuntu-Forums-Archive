---
title: "Trying to create a Ubuntu Wiki page"
date: 2017-03-19
forum: The Cafe
---

### Post by RobGoss on 2017-03-19
Hello everyone, I have been trying to great a **Wiki **page with out any success, each time I click on create a new page I'm greeted with this message

**Message** 
You are not allowed to edit this page

I am login while trying to create the Wiki page so I don't know why I cannot

Thanks so much for any help

---

### Post by ventrical on 2017-03-19
you have to log in with SSO. If you have launchpad account you should be able to create wiki or sign the CoC.

I created mine long ago (before SSO) by just doing-

[http://wiki.ubuntu.com/myusernamehere](http://wiki.ubuntu.com/myusernamehere)

then log in 

I think this is a forum issue we should take up in forums threads.

Regards..

---

### Post by ventrical on 2017-03-19
> **RobGoss said:**
> Hello everyone, I have been trying to great a **Wiki **page with out any success, each time I click on create a new page I'm greeted with this message

**Message** 
You are not allowed to edit this page

I am login while trying to create the Wiki page so I don't know why I cannot

Thanks so much for any help

Yes.. I just tired to create a new wiki page and it bumped me to home page with privlidges.

hmmmnr

---

### Post by ventrical on 2017-03-19
Yeah .. here it is .. you have to have CoC signed.

[https://ubuntuforums.org/showthread.php?t=2334108](https://ubuntuforums.org/showthread.php?t=2334108)

---

### Post by RobGoss on 2017-03-19
Thanks guys for the help, I did sign the COC this morning but it says it's not signed here is the confirmation I received after signing it

Thanks so much for the help with this

---

### Post by RobGoss on 2017-03-19
> **ventrical said:**
> Yeah .. here it is .. you have to have CoC signed.

[https://ubuntuforums.org/showthread.php?t=2334108](https://ubuntuforums.org/showthread.php?t=2334108)

Yes this is the post I was following to find out what was needed

---

### Post by cariboo on 2017-03-19
In order to edit wiki pages, you have to be a member of the [Ubuntu Wiki Editors group]("https://launchpad.net/~ubuntu-wiki-editors"). This was done to stop spammers from creating wiki pages.

---

### Post by RobGoss on 2017-03-19
> **cariboo said:**
> In order to edit wiki pages, you have to be a member of the [Ubuntu Wiki Editors group]("https://launchpad.net/~ubuntu-wiki-editors"). This was done to stop spammers from creating wiki pages.

Aw thank you sir, can anyone join this group? I was pulling the little bit of hair I have left trying to create a page LOL


I think I figured of how to join the Wiki group it says awaiting approval

---

### Post by cariboo on 2017-03-19
> **RobGoss said:**
> Aw thank you sir, can anyone join this group? I was pulling the little bit of hair I have left trying to create a page LOL


I think I figured of how to join the Wiki group it says awaiting approval

Yes, anyone can be a member of the group.

---

### Post by RobGoss on 2017-03-19
**Cariboo,** In post **5#** I added the screen shot I did sign the **COC **,but when viewing on that launchpad website it still looks like it's not signed

---

### Post by jeremy31 on 2017-03-19
From the screenshot, it showed you still had to complete step #3 which is sign it

---

### Post by RobGoss on 2017-03-19
I don't know how I miss that I'm trying to figure out how to sign it, it's telling me to add the contents from this file, **UbuntuCodeofConduct-2.0.txt.asc** in to the **sign box **but I don't see that file on my machine

It also tells me to run this command from the terminal:
```
 gpg --clearsign UbuntuCodeofConduct-2.0.txt
```

But when I do this is what message I receive

```

gpg --clearsign UbuntuCodeofConduct-2.0.txt
gpg: can't open `UbuntuCodeofConduct-2.0.txt': No such file or directory
gpg: UbuntuCodeofConduct-2.0.txt: clearsign failed: file open error

```

Thanks Jeremy31

---

### Post by jeremy31 on 2017-03-19
Do you have a UbuntuCodeofConduct-2.0.txt on your computer?  You need that file and to sign it using your key.  [This](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Signing_Data) might help as it has been a couple years that I signed it

---

### Post by RobGoss on 2017-03-19
Yes I have this file **UbuntuCodeofConduct-2.0.txt** which key are you referring to is the **Key type/ID** that was emailed to me with about 13 numbers

---

### Post by jeremy31 on 2017-03-19
In terminal, navigate to the directory that has the code of conduct file and ```
gpg --clearsign UbuntuCodeofConduct-2.0.txt
```
Then Upload the contents of UbuntuCodeofConduct-2.0.txt.asc on [https://launchpad.net/codeofconduct/2.0/+sign](https://launchpad.net/codeofconduct/2.0/+sign)

---

### Post by RobGoss on 2017-03-19
> **jeremy31 said:**
> In terminal, navigate to the directory that has the code of conduct file and ```
gpg --clearsign UbuntuCodeofConduct-2.0.txt
```
Then Upload the contents of UbuntuCodeofConduct-2.0.txt.asc on [https://launchpad.net/codeofconduct/2.0/+sign](https://launchpad.net/codeofconduct/2.0/+sign)

When I try running that command see in post #12 the results I'm receiving

I don't see any file with this EXT **txt.asc **

---

### Post by deadflowr on 2017-03-19
Are you in the right Directory?

---

### Post by RobGoss on 2017-03-19
Not really sure Deadflowr this is the only file I downloaded and it's in this directory

/home/robert/Downloads/UbuntuCodeofConduct-2.0.txt

---

### Post by jeremy31 on 2017-03-19
This should work ```
cd /home/robert/Downloads
```
```
gpg --clearsign UbuntuCodeofConduct-2.0.txt
```

---

### Post by RobGoss on 2017-03-19
> **jeremy31 said:**
> This should work ```
cd /home/robert/Downloads
```
```
gpg --clearsign UbuntuCodeofConduct-2.0.txt
```

Will running both these commands from the terminal sign the Codeofconduct?

Sorry but it feels like I'm jumping threw hoops :)

---

### Post by jeremy31 on 2017-03-19
I said it should as the normal default directory when opening terminal is home and you need to be in Downloads if that is where the file is

EDIT: I see you got it done

---

### Post by RobGoss on 2017-03-19
> **jeremy31 said:**
> I said it should as the normal default directory when opening terminal is home and you need to be in Downloads if that is where the file is

EDIT: I see you got it done

How did you know Jeremy? LOL thanks to you guys and your patience much appreciated as always 

After running the codes you provided it generated  that **txt.asc** file I needed, I was able to submit the contents into the COC page with success 

Thanks so much now I can try creating the Wiki page when and if I'm excepted in the group

---

### Post by jeremy31 on 2017-03-19
I checked your launchpad page and saw that it said you have signed the Code of Conduct.  I am glad it didn't require more than what it did as I wouldn't have been any help as I signed on April 2, 2015

---

### Post by RobGoss on 2017-03-19
You were a big help my friend thanks so much Now I wanted to create my Wiki page but I waiting because I submitted a request to join the group

See post #7 that Cariboo posted it will explain it

---

### Post by jeremy31 on 2017-03-19
Did you include a link to your forum profile on your launchpad page?  It might speed up the process

---

### Post by RobGoss on 2017-03-19
Not sure what my forum URL link would be would this be correct [https://ubuntuforums.org/member.php?u=1971247](https://ubuntuforums.org/member.php?u=1971247)

---

### Post by jeremy31 on 2017-03-19
That would be correct

---

### Post by RobGoss on 2017-03-19
Ok I see how I can add it thanks so much Jeremy

---

### Post by jeremy31 on 2017-03-19
Not a problem Rob, you might want to change your profile so that the beans(forum posts) are visible

---

### Post by RobGoss on 2017-03-19
Will do Jeremy thanks again have a great evening

---

### Post by wildmanne39 on 2017-03-19
With the change in spam policy about creating wiki pages you have to be an Ubuntu Member to become a member of the wiki group, so if you need help creating a wiki page first you wiull need to contact a staff member by pm that can help you with creating one.

---

### Post by RobGoss on 2017-03-19
Thank you Wildmanne39  for the information much appreciated I will try contacting someone

---

### Post by wildmanne39 on 2017-03-19
> **RobGoss said:**
> Thank you Wildmanne39  for the information much appreciated I try contacting someone
I mean a forum staff member, we can help you, although I am out of practice but I am sure it is like riding a bike.

---

### Post by RobGoss on 2017-03-19
LOL pm is on the way thank you so much

---

