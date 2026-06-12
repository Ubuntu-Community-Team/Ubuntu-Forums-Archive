---
title: "Question marks appear on Apache 2 web pages"
date: 2005-12-20
forum: Server Platforms
---

### Post by R Audano on 2005-12-20
Hello, 
I am having some problems with my web pages whenever I use quotation marks. etc. I get lots of question marks, and little boxes with question marks. I understand this may be due to the type of fonts I select, or because I am using microsoft publishing software. Can anybody enlighten me on this situation?

Thanks,
Robert

System is running Ubuntu 5.04 with Apache 2.

---

### Post by dk_pa on 2005-12-21
I believe that is bad markup by Microsoft.  You could look through and clean the code up or I believe there is an option to clean it automatically in FrontPage and/or MS Word.

Can't tell you too much beyond that.

---

### Post by Juippisi on 2005-12-21
Or it might be your scands. I bet your Ubuntu-server uses UTF-8, but what does your DOCUMENT TYPE say as your locale? Check that too.


I have this:
> <?php
if(strstr($_SERVER['HTTP_ACCEPT'], 'application/xhtml+xml')) { header("Content-Type: application/xhtml+xml");
}
?>
<?php echo '<?xml version="1.0" encoding="ISO-8859-1"?>'; ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="fi">

And server, of course, is ISO-8859.

---

