---
title: "File Uploading In sites - a thought"
date: 2012-05-02
forum: Security
---

### Post by hakermania on 2012-05-02
So, in many websites, like this one, you can upload e.g. attachments, so you select the attachment and click on upload, and the file is being sent to the server.

It seems I am missing something obvious, I don't know many things about HTML or PHP etc, but a thought:
Let's say there's (i) an input box and (ii) a button saying "Select file" (then, after selecting a file, the file's path is being sent to the input box), allowing you to select a file for upload, and lastly, a button that says "Upload".
So, somewhere inside the code, it should say something like this:
```

when Button_Upload_Is_Clicked:
          upload_to_server(input_box->text)

```So, if it said
```

upload_to_server(/etc/passwd)

```would it work the same way?

I mean, what prevents websites from downloading from us anything they want, providing that they know the direct path to get it?

What if pressing the 'Login' button to a website, instead of only logging us in, uploads a local file to the server and then it logs us in?

Don't laugh at me :D

---

### Post by codemaniac on 2012-05-02
A form in an HTML document (Web page) can contain an input element with type="file". This may let the user include one or more files into the form submission. In this case the user is specifying the full path to file that he wants to upload , the html page is not created intelligent enough to haunt for your confidential files in your system and download .

---

### Post by Ms. Daisy on 2012-05-02
I think you're doing what a lot of people do when they don't understand how exploits work (myself included). You dream up an obscure scenario & fret about it.
 
For something like what you're describing to work, the attacker would have to know which browser and version you're using, which operating system and version you're using, and whether you have specific vulnerabilities that would allow such a thing. So a website can't really contain one button to blanketly do what you're saying on every single computer out there. (It would be nice if someone more knowledgeable than me could comment on that though.)
 
The only way I can suggest to ease your mind is to learn about how exploits work & what you can do to defend against them.
 
Links for understanding exploits in a very basic sense:
[http://www.applicure.com/solutions/hacking-attacks](http://www.applicure.com/solutions/hacking-attacks)
[http://en.wikipedia.org/wiki/Exploit_(computer_security](http://en.wikipedia.org/wiki/Exploit_(computer_security))
[http://en.wikipedia.org/wiki/Vulnerability_(computing](http://en.wikipedia.org/wiki/Vulnerability_(computing))
[http://www.ethicalhacker.net/content/view/21/2/](http://www.ethicalhacker.net/content/view/21/2/)
 
And links for securing your computer against many threats are in the security forum stickys and in my signature below:

---

### Post by hakermania on 2012-05-02
But wait one second, while the HTML can ask for downloading from me the path I specified (hey! it's just a path, the webpage doesn't need to know which operating system i am using. The browser doesn't need to mean a lot too! As I think of it, I click on a button and a file dialog comes up, then I select the preferred file and I click open, then the input box is just filled with the path, and the upload button reads the path from the input box so as to upload the file.), it is unable to download a file of its preference? This doesn't sound logical to me.

 I don't have time right now to check your links, but I will learn about uploading using HTML and I will try to do something similar to what I am describing after I check your links of course!

---

### Post by baxterross on 2012-05-03
Browsers prevent Javascript access to the file upload control as well as preventing the kind of exploit you are describing here.
Essentially the file upload dialog box is the only way to input a value into a file upload input element in the html.
Even after the file is selected this way, the full path to the file is obscured from any Javascript code running on the page.
As a developer, I know this because of the hoops I have to jump through when dealing with building file uploading into an application.

---

