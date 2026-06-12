---
title: "cgi output truncation"
date: 2012-01-28
forum: Server Platforms
---

### Post by shumifan50 on 2012-01-28
I have written a program in C++ to handle cgi web requests. It runs fine in a terminal window and all the output that I expect is displayed. When I request it from firefox or IE I get just over 4KB of the 6KB expected. It seems size related, rather than position in the file as the place that it stops varies when I change the text in the first 4KB to make it longer or shorter.
Im running Ubuntu 10.10 with the latest apache2 through updates for it.

I do printf the "content-type: text/html\r\n\r\n" minimum header (I did have more before but have reduced it while trouble shooting).
I then write "<header> ......</header><body>.......</body> where the header has script in it and the body has form definitions etc.

The output stops shortly after the <body> tag, but the exact position varies when I add or remove text earlier in the html script.


Any help greatly appreciated as my development is now stopped dead in its tracks until I can get this to work.

---

### Post by Wayne_V on 2012-01-29
my first thought would be that the i/o buffers aren't getting flushed before your c++ program exits.   try adding a flush and then sleep 1 second before exiting the program and see if that helps ...

---

### Post by shumifan50 on 2012-01-29
@Wayne_V: Thanks for the response.
Yes that was/is my thoughts too, so I have already done a fflush(stdout) and explicitly closed stdout, hoping it would solve the problem. I did however not 'wait' as I thought the fflush would not return before all the data has been written to the 'physical' device= apache in his case.
It definitely looks like a buffer issue, but I cant find anywhere that the mod-cgi buffersizes can be set.
I have also broken the writes into lots of 80 byte writes instead of a single write, but it made no difference.

One last bit of info: If I do a wget of the url, the file I receive is also truncated.

If I cant solve this, I will have to go to writing apache modules, but I like the idea of cgi as a program failure does not bring down the webserver and it makes debugging a breeze.

---

### Post by Wayne_V on 2012-01-29
mod_deflate issue maybe?  

[http://www.gossamer-threads.com/lists/apache/users/407108](http://www.gossamer-threads.com/lists/apache/users/407108)

---

### Post by Wayne_V on 2012-01-29
also, you only need \n for carriage control - that will automatically convert to \r\n on output so by putting in your own \r you are doubling it up.

---

### Post by shumifan50 on 2012-01-29
@Wayne_V:
Thanks, I tried that, made no difference.

I also tried adding sync(), but it also made no difference.

It is a problem with my C++. I have done the following php script(got it from the web) and it works fine. So now for some more digging LOL. I will be in China soon:)

```

<?Php
$file = "/etc/apache2/cgi-bin/templates/EN/header.htm"; //Path to your *.txt file
$contents = file($file);
$string = implode($contents);

echo $string;
?> 


```

---

### Post by shumifan50 on 2012-01-29
Well finally got to the bottom of it:

I broke the output into 80 character lines and output each line, followed by an fflush(stdout)

It seems there is some buffering somewhere that has a limit around 4KB. I will now increase the the amount written in each loop and see where the break point is.

@Wayne_V thanks for your help - appreciated.

---

