# CLIENTE PARA LLAMADAS DE PHP

## Ejemplo de un formulario

Por ejemplo para el login para darnos una idea.

En la pagina login.php tendriamos algo como esto.
```html
<html>
    <body>
        <form action="login_form_handler.php" method="post">
            Name: <input type="text" name="name"><br>
            E-mail: <input type="text" name="email"><br>
            <input type="submit">
        </form>

    </body>
</html>
```
Ya en el archivo login_form_handler.php tendriamos algo como esto.

```php
name = $_POST["name"];
email = $_POST["email"];
// Para enviar los datos
data_array =  array("userName" => name, "email" => email); 
$make_call = callAPI('POST', 'https://yourapi.com/post_url/', json_encode($data_array)); 
$response = json_decode($make_call, true);

if ($response->code == "1") {
    // redirect al menu por ejemplo 
} else {
    // redirigir a la página de que no pudo iniciar sesión.
}

```

Petición GET
```php
$make_call = callAPI('GET', 'https://yourapi.com/post_url/', false);
$response = json.decode($make_call, true);
```

Petición para actualizar PUT
```php
$data_array =  array("data" => "some_update"); 
$update_plan = callAPI('PUT', 'https://yourapi.com/put_url/', json_encode($data_array)); 
$response = json_decode($update_plan, true);
```
