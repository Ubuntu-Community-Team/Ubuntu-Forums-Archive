---
title: "Find File?"
date: 2012-09-05
forum: Ubuntu Studio
---

### Post by chriswt on 2012-09-05
[FONT=Times New Roman][SIZE=3]I’m adding new products to our Web site. As well, removing others. There is a problem that when I remove a product. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]As I understand, the Web page and server was made with Ubuntu 8.1 server, Apache, PHP, MySQL and HTML.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Before I remove the product record through a admin form that was made for easy maintenance. I start off by clicking a button on the form to remove the picture, a jpg file. To check if the jpg file was removed, I open another tab on the Web browser and I view the product. The product picture is still there. I assume the .jpg had not been deleted and the code behind the button is not correct! [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I logon to the Ubuntu 8.1 server as root to look for the .jpg and I EVEN USED SEARCH COMMANDS Exp:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]sudo^find^-iname^FileName[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]find / -name "FileNameBeginning*" -print [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]I CANNOT FIND THE .JPG![/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Attached is a text file of the source code copied from when viewing a product on the Web.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]DO YOU SEE ANYTHING IN THIS CODE THAT TELLS THE DIRECTORY PATH AND/OR DRIVE OR WHERE THE PICs ARE?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]IS THERE A BETTER FORUM TO POST THIS QUESTION?[/SIZE][/FONT]
 
[FONT=Times New Roman]Thank You![/FONT]

---

### Post by spjackson on 2012-09-06
If the file cannot be found on the server, it is reasonable to assume that your attempt at removing it was successful. It is probably still in your browser cache.

I cannot comment on your text attachment because I cannot find it.

Do you have a problem with your capslock key? Or have you overlooked this aspect of the [forum policy]("http://ubuntuforums.org/index.php?page=policy") "ALL CAPS is interpreted as screaming."

---

