# AskMe-Shell

Not exactly a client library, but writeup on how you can use shell to parse askme's data.

## Use Case
[See use case](https://github.com/pirsquare/askme#use-case)

## Requirements
```shell
# You need git and jq to download and parse the json data for askme
# For debian based system
apt-get -y install git jq

# For rpm based system
yum -y install git jq
```

## Examples
```shell

cd /opt && git clone https://github.com/pirsquare/askme.git

# Get list of digitalocean's supported distribution image.
# In this case, we are querying for digitalocean's "dist-image" record
cat data/digitalocean.json | jq '. | [.image.dist[]]'

    Output:
        [
          {
            "id": "centos-5-8-x32",
            "desc": "Centos 5.8 32bit"
          },
          {
            "id": "centos-5-8-x64",
            "desc": "Centos 5.8 64bit"
          },
          {
            "id": "centos-6-5-x32",
            "desc": "Centos 6.5 32bit"
          },
          {
            "id": "centos-6-5-x64",
            "desc": "Centos 6.5 64bit"
          },
          {
            "id": "centos-7-0-x64",
            "desc": "Centos 7.0 64bit"
          },
          {
            "id": "coreos-alpha",
            "desc": "CoreOS Alpha"
          },
          {
            "id": "coreos-beta",
            "desc": "CoreOS Beta"
          },
          {
            "id": "coreos-stable",
            "desc": "CoreOS Stable"
          },
          {
            "id": "debian-6-0-x32",
            "desc": "Debian 6.0 32bit"
          },
          {
            "id": "debian-6-0-x64",
            "desc": "Debian 6.0 64bit"
          },
          {
            "id": "debian-7-0-x32",
            "desc": "Debian 7.0 32bit"
          },
          {
            "id": "debian-7-0-x64",
            "desc": "Debian 7.0 64bit"
          },
          {
            "id": "debian-8-x32",
            "desc": "Debian 8 32bit"
          },
          {
            "id": "debian-8-x64",
            "desc": "Debian 8 64bit"
          },
          {
            "id": "fedora-21-x64",
            "desc": "Fedora 21 64bit"
          },
          {
            "id": "fedora-22-x64",
            "desc": "Fedora 22 64bit"
          },
          {
            "id": "freebsd-10-1-x64",
            "desc": "FreeBSD 10.1 64bit"
          },
          {
            "id": "freebsd-10-2-x64",
            "desc": "FreeBSD 10.2 64bit"
          },
          {
            "id": "ubuntu-12-04-x32",
            "desc": "Ubuntu 12.04 32bit"
          },
          {
            "id": "ubuntu-12-04-x64",
            "desc": "Ubuntu 12.04 64bit"
          },
          {
            "id": "ubuntu-14-04-x32",
            "desc": "Ubuntu 14.04 32bit"
          },
          {
            "id": "ubuntu-14-04-x64",
            "desc": "Ubuntu 14.04 64bit"
          },
          {
            "id": "ubuntu-15-04-x32",
            "desc": "Ubuntu 15.04 32bit"
          },
          {
            "id": "ubuntu-15-04-x64",
            "desc": "Ubuntu 15.04 64bit"
          }
        ]


# Only show ids
cat data/digitalocean.json | jq '. | [.image.dist[].id]'
    Output:
        [
          "centos-5-8-x32",
          "centos-5-8-x64",
          "centos-6-5-x32",
          "centos-6-5-x64",
          "centos-7-0-x64",
          "coreos-alpha",
          "coreos-beta",
          "coreos-stable",
          "debian-6-0-x32",
          "debian-6-0-x64",
          "debian-7-0-x32",
          "debian-7-0-x64",
          "debian-8-x32",
          "debian-8-x64",
          "fedora-21-x64",
          "fedora-22-x64",
          "freebsd-10-1-x64",
          "freebsd-10-2-x64",
          "ubuntu-12-04-x32",
          "ubuntu-12-04-x64",
          "ubuntu-14-04-x32",
          "ubuntu-14-04-x64",
          "ubuntu-15-04-x32",
          "ubuntu-15-04-x64"
        ]


# Get list of google compute engine's supported disk type
# Note: Quoting is required for word "disk-type"
cat data/gcloud.json | jq '. | [.gce."disk-type"[].id]'

    Output:
        [
          "local-ssd",
          "pd-ssd",
          "pd-standard"
        ]


# Get list of aws ec2's region
cat data/aws.json | jq '. | [.ec2.region[]]'

    Output:
        [
          {
            "id": "ap-northeast-1",
            "desc": "Asia Pacific (Tokyo)"
          },
          {
            "id": "ap-southeast-1",
            "desc": "Asia Pacific (Singapore)"
          },
          {
            "id": "ap-southeast-2",
            "desc": "Asia Pacific (Sydney)"
          },
          {
            "id": "eu-central-1",
            "desc": "EU (Frankfurt)"
          },
          {
            "id": "eu-west-1",
            "desc": "EU (Ireland)"
          },
          {
            "id": "sa-east-1",
            "desc": "South America (Sao Paulo)"
          },
          {
            "id": "us-east-1",
            "desc": "US East (N. Virginia)"
          },
          {
            "id": "us-west-1",
            "desc": "US West (N. California)"
          },
          {
            "id": "us-west-2",
            "desc": "US West (Oregon)"
          }
        ]

```

