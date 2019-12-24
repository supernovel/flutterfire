# firebase_core_web

The web implementation of [`firebase_core`][1].

## Usage

### Import the package

To use this plugin in your Flutter app on the web, simply add it as a
dependency in your `pubspec.yaml` alongside the base `firebase_core`
plugin.

_(This is only temporary: in the future we hope to make this package
an "endorsed" implementation of `firebase_core`, so it will automatically
be included in your app when you run your Flutter app on the web.)_

Add this to your `pubspec.yaml`:

```yaml
...
dependencies:
  ...
  firebase_core: ^0.4.1
  firebase_core_web: ^0.1.0
  ...
```

### Updating `index.html`

Due to [this bug in dartdevc][2], you will need to manually add the Firebase
JavaScript file to your `index.html` file.

In your app directory, edit `web/index.html` to add the line:

```html
<html>
    ...
    <body>
        <script src="https://www.gstatic.com/firebasejs/7.5.0/firebase-app.js"></script>
        <script src="main.dart.js"></script>
    </body>
</html>
```

### Initialize Firebase

If you want to initialize the default app, follow the steps in the
[Firebase Web Setup][3] docs. Specifically, you'll want to add the
following lines to your `web/index.html` file:

```html
<body>
  <!-- Previously loaded Firebase SDKs -->

  <script>
    // TODO: Replace the following with your app's Firebase project configuration
    var firebaseConfig = {
      // ...
    };

    // Initialize Firebase
    firebase.initializeApp(firebaseConfig);
  </script>
  <script src="main.dart.js"></script>
</body> 
```

### Using the plugin

Once you have added the `firebase_core_web` dependency to your pubspec,
you can use `package:firebase_core` as normal.

[1]: ../firebase_core/firebase_core
[2]: https://github.com/dart-lang/sdk/issues/33979
[3]: https://firebase.google.com/docs/web/setup#add-sdks-initialize
