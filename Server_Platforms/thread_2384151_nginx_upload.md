---
title: "nginx upload"
date: 2018-02-02
forum: Server Platforms
---

### Post by ELMIT on 2018-02-02
I have installed nginx version: nginx/1.10.3 (Ubuntu)

A website requires to upload files. I use php 7 for handling the upload.

The form:
```

<div class="collapse" id="upload_avatar">
    <div class="card card-body">
        <form enctype="multipart/form-data" action="" method="post">
            <p class="text-left">Upload Avatar:</p>
            <input type="hidden" name="MAX_FILE_SIZE" value="300000" />
            <input name="image" type="file" /><br>
            <button class="form-control mr-sm-2 btn btn-outline-success my-2 my-sm-0" type="submit" name="avatar_upload" aria-controls="collapse_upload_avatar">
                Upload
            </button>
        </form>
    </div>
</div>

```

The php part:
```

if(isset($_POST["avatar_upload"])){
    $verifyimg = getimagesize($_FILES['image']['tmp_name']);

    if($verifyimg['mime'] != 'image/png') {
        echo "Only PNG images are allowed!";
        exit;
    }    

    $uploaddir = '/members/3/';
    $uploadfile = $uploaddir . basename($_FILES['image']['name']);

    if (move_uploaded_file($_FILES['image']['tmp_name'], $uploadfile)) {
        echo "File is valid, and was successfully uploaded.<br>";
    } else {
        echo "Possible file upload attack!<br>";
    }

    echo '<pre>';
    echo 'info:';
    print_r($_FILES);
    print "</pre>";
}

```

It prints out:
> 
Possible file upload attack!
info:Array
(
    [image] => Array
        (
            [name] => Selection_001.png
            [type] => image/png
            [tmp_name] => /tmp/phpGpp3rB
            [error] => 0
            [size] => 299338
        )
)


There is no /tmp/php* file

There is no file in the /members/3/ directory

The permission is 777 for /members and /members/3


nginx/error.log shows: 
PHP message: PHP Warning: move_uploaded_file(/members/3/Selection_001.png): failed to open stream: No such file or directory ... on line 197 PHP message: 
PHP Warning: move_uploaded_file(): Unable to move '/tmp/phpGpp3rB' to '/members/3/Selection_001.png' 


/etc/nginx/nginx.conf:
```

user www-data;
worker_processes auto;
pid /run/nginx.pid;

events {
	worker_connections 768;
	# multi_accept on;
}

http {

	##
	# Basic Settings
	##

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;
	# server_tokens off;

	# server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# SSL Settings
	##

	ssl_protocols TLSv1 TLSv1.1 TLSv1.2; # Dropping SSLv3, ref: POODLE
	ssl_prefer_server_ciphers on;

	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;
	gzip_disable "msie6";

	# gzip_vary on;
	# gzip_proxied any;
	# gzip_comp_level 6;
	# gzip_buffers 16 8k;
	# gzip_http_version 1.1;
	# gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

	##
	# Virtual Host Configs
	##

	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}


```


The sites-available/example.com

```

server {
	listen 80;
	listen [::]:80;

	root /home/ronald/docker-websites/example.com;

	# Add index.php to the list if you are using PHP
	index index.php index.html index.htm index.nginx-debian.html;

	server_name example.com;

	location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ =404;
	}

	location ~ \.php$ {
        	include snippets/fastcgi-php.conf;
        	fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    	}

    	location ~ /\.ht {
        deny all;
    }


    listen 443 ssl; # managed by Certbot
ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem; # managed by Certbot
ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot


    if ($scheme != "https") {
        return 301 https://$host$request_uri;
    } # managed by Certbot


}


```

What am I missing?

---

### Post by ELMIT on 2018-02-06
Am I really the only one on that globe to bump into that problem ??? Huhuhu

---

