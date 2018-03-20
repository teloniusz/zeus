# Zeus server configuration

Here's how you deploy Zeus to a new server. You will need Python 3.6.

First, install `pipenv` (see main `README.md`) and ensure packages are
installed:

    pipenv sync
    pipenv shell

Let's say we want to configure a server as `example.com`, with Zeus available
at `zeus.example.com`.

Make sure you have a server with `nginx` installed and configured. You should
be able to connect to it (using `ssh example.com`) and have sudo rights.

If you want HTTPS, it should have a certificate configured for your server (in
the `http` block).

Copy `hosts_example.yml` to `hosts.yml`, customize.

Create a secrets file with all passwords generated:

    ./generate-secrets secrets/zeus-secrets-example.com.json

Apply with:

    ansible-playbook zeus.yml -i hosts.yml

To just deploy a new version of the code, run:

    ansible-playbook zeus.yml -i hosts.yml -t deploy