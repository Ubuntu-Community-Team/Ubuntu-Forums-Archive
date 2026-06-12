---
title: "New PHP7 Exceptions not recognized - 16.04LTS"
date: 2016-12-17
forum: Server Platforms
---

### Post by Frank P on 2016-12-17
Ubuntu 16.04LTS, PHP7, all updates installed
The new exceptions - Throwable, Error, are not being "Catch"ed.  Happening on 2 servers
Is this likely a problem with my systems or is there a problem with the Ubuntu/php combination.
Is there anything I can check
Thanks
Frank

---

### Post by cariboo on 2016-12-17
Moved here, you may get help quicker here.

Could you post the error message you are getting, or show us part of /var/log/apache2/error.log where the error shows up.

---

### Post by Graham_Willis on 2016-12-17
Frank P: can you demonstrate code which will allow us to determine if these exceptions are caught on our machines? How did you install Apache and PHP7?

---

### Post by Frank P on 2016-12-17
The problem might be that I don't understand the concept - if that's the case please direct me to some reading material. Otherwise, I'm embedding a small php file that I think illustrates the problem. If there's another way to include a file please let me know
Thanks
Frank
```
<?php
try {
  print("<h1>Testing PHP7 Exceptions</h1>");
  print("<p>Submit button will cause a 'variable undefined error' which I thought should be caught by either the Throwable
        or Error exceptions</p>");
  print("<p>however the error gets written to the apache2 error.log but the exception isn't caught</p>");
  print("<p> and the script continues</p>");        
  print("<form action='' method='post'>");
  print(" <input name='Submit1' type='submit' value='submit'>"); 
  print("</form>"); 
  if (isset($_POST['Submit1'])) {
      $x = $abc; 
      print("x = $x");
      print("<h1>???</h1>");
  }
}
catch(Throwable $e) {
    echo $e;
}
catch(ParseError $e) {
    echo $e;
}
catch(Error $e) {
    echo $e;
} 
?>
```

---

### Post by Frank P on 2016-12-17
Sorry, forgot to answer your question.
I don't remember exactly how installed it one server but on the other

```
sudo apt-get install php7.0-mysqlsudo phpenmod pdo_mysql
```

Thanks

Frank

---

### Post by Graham_Willis on 2016-12-20
I suppose that the described problem arises from the fact that "Variable undefined error" is not an exception. It doesn't even generate php error class log entry, but just notice class entry, when it comes to this matter. I believe only exceptions are what is caught. I don't know any specific literature dealing with this topic, but I'm sure there's a lot of information regarding this subject on the web.

---

### Post by Frank P on 2016-12-20
Okay, I guess I misunderstood the Notice error.
I changed the example to cause a ParseError. According to the manual it should throw a ParseError. It writes the error to the log and generates a 500 error. It didn't exho the error as per the Catch. Is that the expected behaviour
I know you can't recover from a Fatal Error but I'm Just trying to understand it all :-)
Thanks
Frank

---

### Post by Graham_Willis on 2016-12-21
[quote="Frank P"]I changed the example to cause a ParseError. According to the manual it should throw a ParseError. It writes the error to the log and generates a 500 error. It didn't exho the error as per the Catch. Is that the expected behaviour[/quote]

I don't know. I'd recommend that you consult PHP documentation. Your questions have much more flavour of programming than system administration, so if you can't find an answer in docs, then I think it'd be best to ask on a PHP programming forum.

---

### Post by Frank P on 2016-12-21
okay, will do.
Thanks
Frank

---

