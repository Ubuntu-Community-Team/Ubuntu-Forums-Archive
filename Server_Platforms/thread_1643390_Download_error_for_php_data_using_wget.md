---
title: "Download error for php data using wget"
date: 2010-12-11
forum: Server Platforms
---

### Post by JL23 on 2010-12-11
I am trying to download data from my server using wget.

I send the login details and store the cookie. I then rotate through n numbers to copy the data into a new file. The saved file is always blank i.e 0kb file size.

My website stores data on individual pages e.g.: (i have changed my actual site name to "mywebsite")
[URL="http://admin.mywebsite.com/index.php/print_view/?html=true&order_id=50"]
[/URL]'http://admin.mywebsite.com/index.php/print_view/?html=true&order_id=50

I am trying to rotate through the numbers 50 to 1 and extract the data from each page. 


The code I am using is below:

#!/usr/bin/perl 

system ("wget --post-data 'username=Test&password=Test&autologin=1' --cookies=on --keep-session-cookies --save-cookies=cookie.txt http://admin.mywebsite.com/index.php/login");

$x = 50;
while ($x <= 1) {
    system ("wget --wait=400 --post-data 'html=true&order_id=50' --referer=http://admin.mywebsite.com/ --cookies=on --load-cookies=cookie.txt --keep-session-cookies --save-cookies=cookie.txt http://admin.mywebsite.com/index.php/print_view/");
    
    system ("wget --post-data 'html=true&order_id=50' --referer=http://admin.mywebsite.com/ --cookies=on --load-cookies=cookie.txt --keep-session-cookies --save-cookies=cookie.txt http://admin.mywebsite.com/index.php/print_view?");
$x++;
}


How do I modify the code above so data is pulled correctly and the saved files are not blank? Thank you

---

