---
title: "CheckGmail (dejó de conectarse)"
date: 2009-10-06
forum: Software
---

### Post by granjero on 2009-10-06
buenas...

quería saber si a alguien le pasó lo mismo?

de repente el checkgmail dejo de conectarse... cuando inicio sesión aparece un cuadrito que dice "Error: wrong user name or password"

el username y el password están bien... 

no se que le pasa!?!?!?

probé con "gmailnotfy" y funciona correctamente pero ese no me gusta...

me gustaría que ande chekgmail...

lo hice correr desde consola a ver si tiraba algún error pero no dice nada hasta que pongo cancelar en el cuadrito y dice lo siguiente


```
jm@pcjm:~$ checkgmail 
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached
jm@pcjm:~$ 

```


salud!

---

### Post by faktorqm on 2009-10-09
esa cosa necesita algun paquete adicional?
algun puerto abierto en el firewall?
algun permiso en particular?
probaste corriendolo con sudo?
donde esta el archivo de configuracion de eso?
antes lo estabas usando y dejo de funcionar luego de un update?
nunca te anduvo?

salu2!

---

### Post by scragar on 2009-10-09
```
checkgmail -update
```?

---

### Post by granjero on 2009-10-09
esa cosa necesita algun paquete adicional? ni idea (lo instalé desde agregar y quitar programas)

algun puerto abierto en el firewall? no que yo sepa

algun permiso en particular? no

probaste corriendolo con sudo? si me tira el mismo error

donde esta el archivo de configuracion de eso? no lo se


antes lo estabas usando y dejo de funcionar luego de un update? lo uso hace muuuuuucho. dejo de andar de buenas a primera sin update de por medio.

nunca te anduvo?

salu2!

[http://mundogeek.net/archivos/2007/12/15/checkgmail-error-incorrect-username-or-password/](http://mundogeek.net/archivos/2007/12/15/checkgmail-error-incorrect-username-or-password/)

ahi comentan el mismo problema que tengo pero siguiendo los pasos que ellos dicen no funca!

salud!

---

### Post by granjero on 2009-10-09
```
jm@pcjm:~$ checkgmail -update
Downloading latest version of checkgmail from SVN ...

Advertencia: HTTP no soporta comodines.
--2009-10-09 23:22:15--  http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
Resolviendo checkgmail.svn.sourceforge.net... 216.34.181.65
Conectando a checkgmail.svn.sourceforge.net|216.34.181.65|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: /viewvc/checkgmail/checkgmail [siguiente]
--2009-10-09 23:22:16--  http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail
Conectando a checkgmail.svn.sourceforge.net|216.34.181.65|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: no especificado [text/plain]
Guardando: «checkgmail»

    [             <=>                       ] 197.112     70,4K/s   en 2,7s    

2009-10-09 23:22:19(70,4 KB/s) - `checkgmail' guardado [197112]



Differences between old and new versions:
diff -urN checkgmail /usr/bin/checkgmail
--- checkgmail	2009-10-09 23:22:19.000000000 -0300
+++ /usr/bin/checkgmail	2009-10-06 23:35:54.000000000 -0300
@@ -455,7 +455,7 @@
 );
 
 my @undo_buffer;
-my ($ua, $cookie_jar);
+my $ua;
 my ($menu_x, $menu_y);
 my @popup_status;
 my $status_label;
@@ -739,7 +739,7 @@
 	# Get the cookie if requested
 	if ($cookies) {		
 		use HTTP::Cookies;
-		$cookie_jar = HTTP::Cookies->new();
+		my $cookie_jar = HTTP::Cookies->new();
 		
 		$ua->cookie_jar($cookie_jar);
 		
@@ -765,7 +765,7 @@
 			# deciphering the login form! :)
 			unless ($hosted) {
 				# Normal Gmail login action ...
-				$error = http_get("Email=".$URI_user."&Passwd=".$URI_passwd, "LOGIN");
+				$error = http_get("https://www.google.com/accounts/ServiceLoginAuth?ltmpl=yj_wsad&ltmplcache=2&continue=https%3A%2F%2Fmail.google.com%2Fmail%3F&service=mail&rm=false&ltmpl=yj_wsad&Email=$URI_user&Passwd=$URI_passwd&rmShown=1&null=Sign+in", "LOGIN");
 
 				$cookie_jar->scan(\&scan_at);
 				unless ($error || !$gmail_sid || !$gmail_gausr) {
@@ -879,75 +879,60 @@
 		return;
 		
 	} elsif ($method eq 'LOGIN') {
-		# New LOGIN method written by Gerben van der Lubbe on Oct 6, 2009.
-		# (based in turn on vially's (https://sourceforge.net/users/vially/) PHP code.
-		
-		# Well, we did get a URL here, but it doesn't make any sense to send both LOGIN and the URL to this function.
-		# So, this URL is just the username and password addition.
-		my $req = HTTP::Request->new('GET' => "https://www.google.com/accounts/ServiceLogin?service=mail");
+		# a further hack to streamline the cookie login process
+		my $req = HTTP::Request->new('GET' => "$address");
+
 		my $response = $ua->request($req);
-		if($response->is_error) {
-			my $code = $response->code;
-			my $message = $response->message;
-			$error = "Error: $code $message";
-			$http_status->enqueue($error);
-			return $error;
-		}
-		my $http = $response->content;
+		# if(! $response->is_success) {
+    		# print "### $address\n => ", $response->status_line, "\n"
+  		# } elsif($response->previous and $response->previous->is_redirect) {
+    		# print "## Moved $address\n## => ", $response->request->url, "\n";
+  		# } else {
+    		# print "## OK: $address\n";
+  		# }
 
-		# Find the value of the GALX input field
-		if($http !~ m/<input[^>]+name="GALX"[^>]*value="([^"]*)"/ig) {
-			return "Error: No GALX input field found";
-		}
-		my $post_galx = URI_escape(URI_unescape($1));
-		# my ($post_galx) = ($http =~ m/"GALX".*?value="(.*?)"/ismg) || return "Error: No GALX input field found";
-		# $post_galx = URI_escape(URI_unescape($post_galx));
-
-		# Find the data to post
-		my $post_data;
-		$post_data = "ltmpl=default&ltmplcache=2&continue=http://mail.google.com/mail/?ui%3Dhtml&service=mail&rm=false&scc=1&GALX=$post_galx&$address&PersistentCookie=yes&rmShown=1&signIn=Sign+in&asts=";
-		print "Logging in with post data $post_data\n" unless $silent;
-
-		# Send the post data to the login URL
-		my $post_req;
-		my $post_response;
-		$post_req = HTTP::Request->new('POST' => "https://www.google.com/accounts/ServiceLoginAuth?service=mail");
-		$post_req->content_type('application/x-www-form-urlencoded');
-		$post_req->content($post_data);
-		$post_response = $ua->request($post_req);
-		if($post_response->is_error) {
+		if ($response->is_error) {
 			my $code = $response->code;
 			my $message = $response->message;
 			$error = "Error: $code $message";
 			$http_status->enqueue($error);
-			return $error;
 		}
-		my $post_http = $post_response->content;
-
-		# Find the location we're directed to, if any
-		if ($post_http =~ m/location\.replace\("(.*)"\)/) {
-			# Rewrite the redirect URI.
-			# This URI uses \xXX. Replace those, and just to be sure \\. \" we don't handle, though.
-			my $redirect_address = $1;
-			$redirect_address =~ s/\\\\/\\/g;
-			$redirect_address =~ s/\\x([0-9a-zA-Z]{2})/chr(hex($1))/eg;
-			print "Redirecting to ".$redirect_address."\n" unless $silent;
-
-			# And request the actual URL
-			my $req = HTTP::Request->new('GET' => $redirect_address);
-			my $response = $ua->request($req);
-			if($response->is_error) {
-				my $code = $response->code;
-				my $message = $response->message;
+		my $http = $response->content;
+		my $code = $response->code;
+		my $message = $response->message;
+		
+		# New google accounts use a strange javascript/meta-refresh redirect ...
+		# ... but we catch them with this! :)
+		if ($http =~ m/location\.replace\("(.*)"\)/) {
+			my $new_addr = $1;
+			$new_addr =~ s/\\u003d/=/g;
+			$new_addr =~ s/\\x3d/=/g;
+			$new_addr =~ s/\\075/=/g;
+			$new_addr =~ s/\\46/&/g;
+			$new_addr =~ s/\\x26/&/g;
+			$new_addr =~ s/\\75/=/g;
+			return unless $new_addr =~ m/^http/i;
+			$new_addr =~ s/^http(?!s)/https/;
+			
+ 			print "\nNew login method: manually following redirect address $new_addr ...\n\n" unless $silent;
+			
+			my $req2 = HTTP::Request->new('GET' => "$new_addr");
+			my $response2 = $ua->request($req2);
+			# if(! $response->is_success) {
+    			# print "### $address\n => ", $response->status_line, "\n"
+  			# } elsif($response->previous and $response->previous->is_redirect) {
+    			# print "## Moved $address\n## => ", $response->request->url, "\n";
+  			# } else {
+    			# print "## OK: $address\n";
+  			# }
+			if ($response2->is_error) {
+				my $code = $response2->code;
+				my $message = $response2->message;
 				$error = "Error: $code $message";
 				$http_status->enqueue($error);
-				return $error;
 			}
+			# my $http = $response2->content;
 		}
-		else {
-			print "No location.replace found in HTML:\n".$post_http unless $silent;
-		}
-		
 		return $error;
 		
 	} elsif ($method eq 'LOGOUT') {
@@ -3236,14 +3221,7 @@
 sub URI_escape {
 	# Turn text into HTML escape codes
 	($_) = @_;
-	s/([^a-zA-Z0-9])/$escapes{$1}/g;
-	return $_;
-}
-
-sub URI_unescape {
-	# Turn HTML escape code into text
-	($_) = @_;
-	s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
+	s/(.)/$escapes{$1}/g;
 	return $_;
 }
 




OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)> y
Update NOT performed ...
Deleting temp file ...
Continuing with application startup ...

Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached
jm@pcjm:~$ 

```

---

### Post by faktorqm on 2009-10-11
fijate si te quedo el archivo checkgmail desde donde te lo bajaste (sino hace 

```
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
```

) y despues hace

```
sudo mv checkgmail /usr/bin/
```

y ahi lo actualizas vos a mano. salu2!

---

### Post by Sleeping Beauty on 2009-10-12
A mi tampoco me funciona. Pero no por invalid password sino que se queda autentificando el usuario y no se conecta. Ya le hice update y nada...

---

### Post by pablo.s on 2009-10-12
> **Sleeping Beauty said:**
> A mi tampoco me funciona. Pero no por invalid password sino que se queda autentificando el usuario y no se conecta. Ya le hice update y nada...

Debe tener algún problema con el
protocolo seguro https. Puede que
no negocie bien los certificados.
Desde el navegador te funciona bien?

---

### Post by granjero on 2009-10-12
si gmail me anda desde el firefox3.5 y también probé otros chequeadores de mails... el gmailnotify por ejemplo anda bien...

desisntalé desde synaptic y puse remover completamente!

después desde consola puse 
sudo aptitude install checkgmail

se instaló y anduvo....

facktorm con esos pasos no había funcionado!

pero ya le pongo la caratula de solved!

gracias a todos por su ayuda!

salud!

---

### Post by granjero on 2009-10-13
cuando prendí la pc el día de hoy me tiro el mismo error...

así que no esta "solved" el tema!

salud!

---

### Post by tatsuno on 2009-10-13
A mi me pasaba lo mismo hasta hoy que he hecho:
```
checkgmail -update
```
y se ha solucionado.

---

### Post by sitiomatic on 2009-10-13
> **faktorqm said:**
> fijate si te quedo el archivo checkgmail desde donde te lo bajaste (sino hace 

```
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
```

) y despues hace

```
sudo mv checkgmail /usr/bin/
```

y ahi lo actualizas vos a mano. salu2!

Probado pero en mi caso no funciona.
Gracias

---

### Post by tatsuno on 2009-10-14
Yo antes de hacer el checkgmail -update lo desinstale entero, borre el directorio .checkgmail de mi home y lo volvi a instalar. Despues hice el update, configure de nuevo mi cuenta y funciono.

---

### Post by sitiomatic on 2009-10-14
> **tatsuno said:**
> Yo antes de hacer el checkgmail -update lo desinstale entero, borre el directorio .checkgmail de mi home y lo volvi a instalar. Despues hice el update, configure de nuevo mi cuenta y funciono.

Acabo de hacer lo mismo y el mio sigue sin funcionar.......grrrrrrr

---

### Post by tatsuno on 2009-10-14
Yo cuando lo desinstale use la opcion purge. Y despues de reinstalarlo hice checkgmail -update. Tengo la beta de Karmic.

---

### Post by Sleeping Beauty on 2009-10-14
Sitio estoy igual! No funciona... Será que hay que evolucionar a Karmic???:lolflag:

---

### Post by sitiomatic on 2009-10-14
> **Sleeping Beauty said:**
> Sitio estoy igual! No funciona... Será que hay que evolucionar a Karmic???:lolflag:

Yo voy de a poquito, ahora uso jaunty con kernel 2.6.31.
No es la primera vez que pasa esto con el checkgmail, suelen arreglarlo rapido.
Me gustaba el checkgmail porque le podia poner sonido y enterarme si llego un mail cuando estoy tirando en la cama en vez de estar trabajando :)
El nuevo notifier que encontre (ver post sobre eso) tambien tiene sonido asi que por ahora estoy bien.

---

### Post by granjero on 2009-10-15
logré que ande... pero no tan bien como antes....

lo que hice fue desinstalar desde agregar y quitar y volver a instalar desde consola.

después también desde consola hice:

```
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail
```

con esto me funciona...  pero ahora cuando le doy click al icono de notificación no entra directo al webmail sino que queda en la pantalla de login y tengo que darle aceptar....

antes le daba click al iconito y entraba directamente al mail... pero peor es nada...

salud!

---

### Post by sitiomatic on 2009-10-15
Yo hice lo que vos hiciste pero cuando lo ejectuto me sale una ventana que duce que me falta el Crypt::SSLeay que no tengo ni idea que es.

---

### Post by jpmorelli on 2009-10-16
> **granjero said:**
> logré que ande... pero no tan bien como antes....

lo que hice fue desinstalar desde agregar y quitar y volver a instalar desde consola.

después también desde consola hice:

```
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail
```

con esto me funciona...  pero ahora cuando le doy click al icono de notificación no entra directo al webmail sino que queda en la pantalla de login y tengo que darle aceptar....

antes le daba click al iconito y entraba directamente al mail... pero peor es nada...

salud!

Gracias Granjero, con esto lo solucioné. No uso lo del acceso a Gmail mediante el click asi que me quedó andando joya.

---

### Post by Carlos C on 2009-10-30
> **granjero said:**
> 

```
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail
```

salud!

Me sirvió, gracias.

---

