---
title: "Job interview, Need help with learning some commands?"
date: 2020-02-12
forum: Ubuntu, Linux and OS Chat
---

### Post by phoop007 on 2020-02-12
Hey! :)

I am trying to learn some basic Terminal commands, for my new job interview I am studying some very basic commands.

Anyone have a good resource to find these types of commands, or you know off the top of your head? 

Thanks!

I want to Display the system information
I want to Display the system network connections
I want to Display who you I am logged in as
I want to Display the directory I am working in
I want to List all of the files in the directory
I want to Create a file with my name
I want to Create a directory with my name
I want to Copy the file into the new directory.
I want to Display the file in the new directory
I want to Delete the directory.
I want to Show the disk partitions

---

### Post by wildmanne39 on 2020-02-12
Hello and welcome to the forum.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by him610 on 2020-02-12
Hello phoop007,

Welcome to the forums. We were all newbies at one time.
You can find it all here, [http://linuxcommand.org/tlcl.php]("http://linuxcommand.org/tlcl.php")
It can be downloaded it for free.

---

### Post by mastablasta on 2020-02-13
also, if i was in the business of hiring people i would hire those that learn fast. knowledge is good, but experience with knowledge still beats it.

we had some temps that just couldn't learn the steps. it was all too ethereal for them. we had some that learned fast even though they had no knowledge or prior experience in commerce. they were then offered a 1 year contract, where they further improved and showed that previous 2 months of good work was not just a coincidence. after that, they got a permanent contract. i did push the management a bit for that 1 year contract because i saw the potential and i saw they learned fast.  i was right.

---

### Post by TheFu on 2020-02-13
All those things are extremely basic.  Any $4 used Beginning Unix book will have them from a used book store - the age of the book doesn't matter, much.  TLCL (book link provided by him610 above) is probably the most efficient way to learn that stuff and much more, for free.

Don't forget that there are manpages on almost every Linux/Unix computer.  To learn more, **man man**

Google will find *Unix command summary sheets*, if that is what you seek.  Let's see what google finds when I search that .... yep, 5,000,000+ results including many 1 page PDF images to print.

If someone claimed to know Linux and didn't know those and 50 other commands, it would be clear in less than 3 minutes. To me, the list above looks like the 1st week homework assignment for a beginning Unix shell class.  Getting system information is the only one that would be different based on the current version of an OS you are on.  There is no built-in system info command, but there are a few that can be installed. It is a matter of personal preference on a personal system, but at work, they probably don't allow those tools to be installed, so you'll need to run 20 commands to get the different parts of information about a system.  **inxi** and **lshw** are some tools that I like on my systems, but aren't installed with the OS. Also, both don't show **all** the information - inxi doesn't recognize my USB network adaptor, for example. If that is what you care about, it is a useless tool.

Knowing how to find answers is more important than actually knowing any specific answer.

---

### Post by EuclideanCoffee on 2020-02-13
This taught me everything I know. [https://www.tldp.org/LDP/abs/html/index.html](https://www.tldp.org/LDP/abs/html/index.html)

---

