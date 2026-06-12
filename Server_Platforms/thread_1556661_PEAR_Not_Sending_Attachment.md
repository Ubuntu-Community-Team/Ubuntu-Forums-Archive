---
title: "PEAR Not Sending Attachment"
date: 2010-08-19
forum: Server Platforms
---

### Post by bumcheekcity on 2010-08-19
```

  $result = mysql_query('SELECT * FROM tablename');
  while ($row = mysql_fetch_assoc($result))
  {
    echo '<p>Sending Mail to '.$row['fullname'].' about wards "'.$row['wards'].'"...';
    
    $mime = new Mail_mime('');  
    $mime->setTXTBody('Text version of email');
    $mime->setHTMLBody('<html><body>HTML version of email</body></html>');
    $body = $mime->get();
    $hdrs = $mime->headers($hdrs);
    
    $file = '.\path\to\filename.csv';
    
    if (file_exists($file))
    {
      echo 'file exists';
    } else {
      echo 'no file';
    }

    $mime->addAttachment($file, 'text/csv', 'filename.csv');
    $mail =& Mail::factory('smtp', $params);
    $mail->send($row['email'], $hdrs, $body);
    if (PEAR::isError($mail)) 
    {
      echo('<p>Mail not sent to '.$row['email'].' because of '.$mail->getMessage().' with wards '.$row['wards'].'.</p>');
    } else {
      echo('<p>Message successfully sent to <b>'.$row['email'].'</b> with wards '.$row['wards'].'.</p>');
    }
    echo '</p>';
    die();
  }
?>
```

This code sends the email fine, but with absolutely no attachment at all. I've send attachments with emails from the same server using PEAR and a similar setup before, so what's going wrong? This is a windows server, by the way, and the two IF statements there give me success statsments.

---

