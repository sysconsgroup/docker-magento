## How to start the project

### Get the access!

Ask to your TL (or to the magic Marco Patania) to give you the right access grants to:

  https://bitbucket.org/sysconsgroup/workspace/projects/SPS

### Automated Setup (New Project)

```bash
# Create your project directory then go into it:
mkdir -p ~/your/path/to/workspace/magento
cd $_

# Run this automated one-liner from the directory you want to install your project.
curl -s https://raw.githubusercontent.com/sysconsgroup/docker-magento/master/lib/onelinesetup | bash -s -- magento.test 2.4.7 community
```

The `magento.test` above defines the hostname to use, and the `2.4.7` defines the Magento version to install. Note that since we need a write to `/etc/hosts` for DNS resolution, you will be prompted for your system password during setup.

After the one-liner above completes running, you should be able to access your site at `https://magento.test`.


### Install sample data

After the above installation is complete, run the following lines to install sample data:

```bash
bin/magento sampledata:deploy
bin/magento setup:upgrade
```

### Access to your backend

To access your Magento 2 backend, you have in order to disable the TFA (Two Factor Authentication) and to create an Admin user.

#### Disable TFA 

To disable TFA, simply run those commands into your Magento project folder

```bash
bin/magento module:disable {Magento_AdminAdobeImsTwoFactorAuth,Magento_TwoFactorAuth}
bin/magento cache:flush
```

#### Create your Admin user

To create an Admin user, run this command and follow the instruction (tip: the password must have a min lenght of 8 chars and contain letters and numbers)

```bash
bin/create-user
```

## Congratulation!
Now you will be able to see the container into your Docker Desktop installation or to run it with `docker-compose up` or `docker compose up`