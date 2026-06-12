---
title: "HTML/XML experts - I need a little help"
date: 2014-04-20
forum: The Cafe
---

### Post by Sylvester the Cat on 2014-04-20
I wasn't quite sure where to put this so I figured on just putting it here. I need a little assistance to figure out the best way to do this. Here is the situation in a nutshell. 

I want to create a database editing program that is HTML/CSS/Javascript based. That is I want to be able to run this editing program in a browser and update xml files based on the information the user puts in. I realize that Javascript will not write to client side files and that I need to be on the server-side of things to do this. PHP looks like it might be a solution but I'm wondering if the client is going to need to install anything on their end to make it work. I am trying to find the more noninvasive solution for the client so they can just open up the program in their browser and edit away. I don't want to have to make them install other things to make this work. However if there is no other way to write to a file, then I guess I'm stuck doing it that way. 

One solution I was looking into was through AJAX. This is what I have now. 

```

    $.ajax({
        url: 'RacesFromCoreRules.xml',
        data: $(xml).text(), 
        type: 'POST',
        contentType: "text/xml",
        dataType: "xml",
        success : function(){alert("Database Updated");},
        error : function (xhr, ajaxOptions, thrownError){ 
            alert("Update failed");     
            console.log(xhr.status);          
            console.log(thrownError);
        } 
    });

```

this is not working. It is not updating the file. It returns as succeeded but the file is not updated. Does anyone see what might be the problem here? Is AJAX not a good solution? Is there a better solution? :confused: Thanks a lot! :P

---

### Post by SeijiSensei on 2014-04-21
If the XML files will reside on the server, PHP is a fine choice.  It would even work if the files were to be delivered to the client, though you'd need to create the files first, then give the user a download link when they are complete.

You will have to pay attention to directory permissions, though.  The web server software runs as an unprivileged user named www-data.  You'll need to make sure that the location(s) where any files are stored are writable by that user.  For the create-then-download model, you can just put the file in /tmp where everyone has write privileges.  For that reason you should delete it immediately after it is downloaded if privacy matters.

---

### Post by Sylvester the Cat on 2014-04-21
The xml files will definitely be with the client, although I don't believe the files will reside on a server on their end. It would be like downloading software, running the install application and installing all the files necessary to run the application which include these xml files which encompasses the database.

---

### Post by lykwydchykyn on 2014-04-22
You can't post to a local file.  

Your URL in the ajax request needs to point to a URL on a server that can accept an HTTP post request and do something meaningful with it.  You can do that bit in PHP, Python, Ruby, node.js, Java, Perl, or any language with a CGI library; pick your favorite.

If you want to write a local application, you should probably look into a different technology stack; web browsers are too sandboxed for this purpose.

---

### Post by Sylvester the Cat on 2014-04-22
hmm... I do have alternatives. I was looking into PHP but I don't think I want to force users into installing it on their end. I guess I'll just move the project back to C++. Thanks!

---

### Post by SeijiSensei on 2014-04-22
PHP really isn't designed for client workstations.  It's intended for writing server-side web applications.  Users cannot really "install" PHP.  (There is a command-line implementation that you can invoke on a workstation, but there are much better language choices for a client-side application.)

---

### Post by lykwydchykyn on 2014-04-22
> **Sylvester the Cat said:**
> hmm... I do have alternatives. I was looking into PHP but I don't think I want to force users into installing it on their end. I guess I'll just move the project back to C++. Thanks!

If you want a front-end that's "HTMLish" (Declarative syntax, javascriptish automation, Stylesheets, etc), you might look at using QML for the GUI.  It's part of QT so it meshes nicely with a C++ backend.

---

