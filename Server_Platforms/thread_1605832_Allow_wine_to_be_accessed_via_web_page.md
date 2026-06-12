---
title: "Allow wine to be accessed via web page"
date: 2010-10-25
forum: Server Platforms
---

### Post by Ahriman on 2010-10-25
I recently got the 'OK' from upstairs to move my development web server from the busted down Vista machine to a new Ubuntu server. I did the server install this morning, and the web portion is working well.

One of the scripts we use, however, called a file 'pdftk.exe' with some arguements which, in effect, took $_POST data and populated a PDF fdf form with it, creating a new PDF file with the $_POSTed information in the form fields. This worked fine when it was running on the Vista machine, but I've run into a snag getting it working on Ubuntu.

I bit the bullet and installed wine (and all the junk that comes with it). My passthru() command in the PHP script now looks like this:

[PHP]$command = 'wine pdftk.exe '.$pdf_file.' fill_form '.$fdf_file .' output "'.$fname.'" flatten';
passthru($command);[/PHP]

My problem is that it's not actually calling the pdftk.exe program at all. I can get it to work if I manually run the command (when logged on as 'user' (default user)), or if I put that line in a new php file and run it from the command line (php test.php) but I can't figure out how to get it to run when it's accessed via a web page.

I have changed the permissions on the directory where the pdf file is to be created to be owned by www-data, and I've made www-data the owner of the pdftk.exe file, and also set it to chmod 775 just in case.

I think at this stage it's wine not letting www-data call it, but I could be wrong. How do I go about getting this command working?

**Edit: found the issue. I copied my ~/.wine folder to /var/www and in my script I prefix the wine command with 'HOME=/var/www'.**

---

