---
title: "AWS S3 static webpage questions"
date: 2017-07-19
forum: Server Platforms
---

### Post by Drone4four on 2017-07-19
I am looking to experiment with AWS's Hosting A Static Website on S3. "Static" in this case means *no server side backend computing, like PHP or .NET*.  That's what Ryan Kroonenburg says in his **A Cloud Guru** udemy course. And that's what it says in the aws docs:

> 
You can host a static website on Amazon Simple Storage Service (Amazon S3). On a static website, individual web pages include static content. They might also contain client-side scripts. By contrast, a dynamic website relies on server-side processing, including server-side scripts such as PHP, JSP, or ASP.NET. Amazon S3 does not support server-side scripting. Amazon Web Services (AWS) also has resources for hosting dynamic websites. To learn more about website hosting on AWS, go to Websites and Website Hosting.

([source]("http://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html"))

My question: If I were to include the following sample disqus code:
```

<div id="disqus_thread"></div> <!-- begin disqus -->
<script>
/**
* RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
* LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
*/
/*
var disqus_config = function () {
this.page.url = PAGE_URL; // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');

s.src = '//<DN1>.disqus.com/embed.js';

s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
<!-- end disqus --> 
```

...would that parse and function exactly as it would on a regular webserver?  I would think so because I understand that the comments made are stored on the disqus network and my S3 instance would not have to interface with a database hosted on AWS.  Am I right?

Another question: What about javascript code like for Google Analytics such as this?

```

  <!-- Google Analytics -->
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-71595941-1', 'auto');
  ga('send', 'pageview');

</script>
<!-- End Google Analytics -->

```
```

 <!-- Google Tag Manager -->
<noscript><iframe src="//www.googletagmanager.com/ns.html?id=GTM-T3WKDW"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-T3WKDW');</script>
<!-- End Google Tag Manager -->

```

---

### Post by j.deijns on 2017-07-20
Yes, you are right. As long as all the content is stored on the Disqus servers (which is the case) and you only host HTML, CSS and Javascript on your hosting it will work just like a regular hosting. The Google Analytics will also work.

---

### Post by Drone4four on 2017-07-21
> **j.deijns said:**
> Yes, you are right. As long as all the content is stored on the Disqus servers (which is the case) and you only host HTML, CSS and Javascript on your hosting it will work just like a regular hosting. The Google Analytics will also work.

Thank you, **@j.deijns**, for answering my question.  I am honoured that you decided to create an Ubuntu Forum account just to answer my question. :D

---

### Post by Habitual on 2017-07-21
and since S3 is Storage only, the statement "Amazon S3 does not support server-side scripting" is "accurate".

---

