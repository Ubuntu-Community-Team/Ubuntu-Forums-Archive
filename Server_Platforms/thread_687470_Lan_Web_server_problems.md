---
title: "Lan Web server problems"
date: 2008-02-04
forum: Server Platforms
---

### Post by pbreah on 2008-02-04
I have 2 PCs:

One has Ubuntu and the other Windows Vista.

The purpose of the Ubuntu PC is to serve as a testing Web server. The other Windows Vista PC is to do the actual work of development.

I can access the Web server on the local network network by typing in my browser (on the Windows Vista PC):

[http://192.168.2.19/pathtoWebsite/](http://192.168.2.19/pathtoWebsite/)

The problem is the path to the images, css files and links are not correct when viewed on the windows pc

All the paths to the images and links start with: [http://localhost/](http://localhost/).. some start with a relative paths: /default/images/...

The end result is a page that renders incorrectly. The only way that the Website renders correctly is by opening the Website on the same server.

Please advice how to make the LAN Web Server render correctly on any computer on the local network, not just on the same server.

Thank you.

---

### Post by hyperair on 2008-02-04
The problem is with your HTML files, not with the web server. Could you post one of the problematic HTML files here?

---

### Post by pbreah on 2008-02-04
It can't be the HTML files, because any website I try to open does the same thing. Below is a fragment of the HTML code php generated on the windows Vista PC.

On the server the Website renders correctly because all the references to localhost are correct since the server is "serving" the files, but when the references are generated on the client (windows PC) the references to localhost refer to the same computer that is viewing, but not serving the files. That is why the page links and images are broken.

Any other ideas?


[HTML]
<div id="container">

  
  <div id="header"><div class="a"></div>
<div class="b"><a href="http://localhost/opencart/index.php?controller=home">Home</a><a href="http://localhost/opencart/index.php?controller=account">Account</a>
    <a href="http://localhost/opencart/index.php?controller=account_login">Log In</a>
    <a href="http://localhost/opencart/index.php?controller=cart">Basket</a><a href="http://localhost/opencart/index.php?controller=checkout_shipping">Checkout</a></div>

</div>

  
  <div id="bar">

    
    <div class="language">
    <form action="http://localhost/opencart/index.php?controller=home" method="POST" enctype="multipart/form-data">
    <div>
      <input type="image" src="catalog/template/default/image/en.png" alt="English"/>
      <input type="hidden" name="language" value="en"/>
    </div>

  </form>
  </div>

    
    
    <div class="currency">
  <form action="http://localhost/opencart/index.php?controller=home" method="post" enctype="multipart/form-data" id="currency">
    <div>
      <select name="currency" onchange="document.getElementById('currency').submit();">
                        <option value="USD">US Dollar</option>
                                <option value="EUR">Euro</option>

                                <option value="GBP" SELECTED>Pound Sterling</option>
                      </select>
    </div>
  </form>
</div>[/HTML]

---

### Post by hyperair on 2008-02-05
Well you seem to know what's the problem, so I won't bother explaining that. Replace "http://localhost/" with just "/". "/" refers to the root of the server, no matter what URL you use. "http://localhost/" will refer only to the local server. If the local server doesn't have files, you will have issues. Believe me when I say you don't want to put [http://localhost/](http://localhost/) there.

---

