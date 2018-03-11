# gitlab-irc

## Summary
A lightweight gitlab irc bot that announces gitlab project notifications via webhooks.

## Credits
Forked from dvdmuckle/docker-gitlab-irc. Original project by chkelly/gitlab-irc.

## Supports
* Connecting to an IRC server over SSL
* Authing with Nickserv
* Support for announcing Commits, Merge Requests, Tags, and Issues.

## Requirements
* Tested on Ruby 2.3.0
* Tested with Gitlab CE 8.5

## Configuration

The following parameters can be set either in the config.yml file or via environment variables.

| Option            | Example Value    | Description                                       | Required? | Default        |
|-------------------|------------------|---------------------------------------------------|-----------|----------------|
| IRC_HOST          | irc.freenode.com | IRC Server Hostname                               | Yes       |                |
| IRC_PORT          | 6667             | IRC Server Port                                   |           | 6667           |
| IRC_PASSWORD      | sample_password  | Server Password                                   |           |                |
| SSL               | true             | if true, allows connection to irc server over ssl |           | false          |
| IRC_CHANNELS      | ['#dev','#all']    | Array of channels to join                         | Yes       | ['#gitlab-irc'] |
| IRC_NICK          | GitLab           | Bot Name                                          |           | GitLab         |
| IRC_REALNAME      | GitLabBot        | Real Name                                         |           | GitLabBot      |
| IRC_USER_NAME     | gitlab-irc       | Username for authing with nickserv                |           |                |
| IRC_USER_PASSWORD | user_password    | Password for authing with nickserv                |           |                |
| GITLAB_TOKEN | sample_token    | Secret X-Gitlab-Token header used to authenticate requests                |           |                |
| DEBUG             | true             |                                                   |           | false          |

## Installation
### Docker

Start the gitlab-irc server with at least IRC_HOST and IRC_CHANNELS environment variables set:

```bash
docker run -e IRC_HOST=irc.freenode.com -e "IRC_CHANNELS=['#gitlab-irc']" -e IRC_NICK=gitlab-9875 -d -p 5000:5000 --restart=always --name gitlab-irc dvdmuckle/gitlab-irc:latest
```

### Configure Projects within Gitlab

Within Gitlab CE, select a project, then go to Settings -> Hooks, and enter in the below. Check all the boxes. Adjust the below host and port to point to the ip:port that the gitlab-irc service is running on.

```bash
http://localhost:5000
```
