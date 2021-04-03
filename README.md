# Whatsapp

Whatsapp desktop client for linux.

# Installation

You need to have the latest version of [docker](https://docs.docker.com/get-docker/) installed.

You will have to clone the repository.

```bash
git clone git@github.com:tjventurini/whatsapp.git
```

Next you will have pull the [nativefier](https://github.com/nativefier/nativefier) container in order to build the application.

```bash
docker pull nativefier/nativefier
```

Now you can build the electron application using the following command.

```bash
docker run --rm -v /home/thomas/codes/apps/whatsapp:/src -v /tmp:/target nativefier/nativefier --icon /src/icon.png --name whatsapp -p linux -a x64 --single-instance --tray --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.90 Safari/537.36" https://web.whatsapp.com/ /target/
```

Now you can copy the build wherever you want.

```bash
mv /tmp/whatsapp-linux-x64 ~/apps/whatsapp
```

Now you can add an app launcher as shown below and store it under `~/.local/share/applications/whatsapp.desktop`.

```
[Desktop Entry]
Type=Application
Version=1.0
Exec=/home/username/apps/whatsapp/whatsapp
Name=Whatsapp
Comment=Custom whatsapp client for linux.
Icon=/home/username/apps/whatsapp/icon.png
Terminal=false
Categories=Media
```

Don't forget to refresh the database of application entries afterwards 😉

```bash
update-desktop-database ~/.local/share/applications
```