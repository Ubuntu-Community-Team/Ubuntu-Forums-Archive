---
title: "Comando Shell_exec de PHP en Ubuntu."
date: 2012-10-18
forum: Software
---

### Post by proteus8 on 2012-10-18
Hola a todos, tengo el siguiente código con el cual le puedo hacer un ping a un pc cualquiera dentro de mi red e identificar si esta o no respondiendo.
Este código funciona bien en windows, pero necesito que funciones en ubuntu, e leído por Internet que hay que dar permisos al usuario de apache "www-data" lo hice pero no se porque sigue sin funcionar mi código me podrían ayudar por favor.

<?php 
ini_set('display_errors', 'On'); 
ini_set('display_errors', 1); 
set_time_limit(3600); 
error_reporting(E_ERROR | E_WARNING | E_PARSE | E_NOTICE); 
error_reporting(E_ALL); 
error_reporting(-1); 
    $ip = "10.70.1.129"; 
    $output = shell_exec("echo 'clave_root' | sudo -u root -S ping $ip"); 
    if (strpos($output, "recibidos = 0")) { 
    echo  $estado; 
    }else{ 
    $estado='Conectado'; 
        echo  $estado; 

    } 
    ?>

---

