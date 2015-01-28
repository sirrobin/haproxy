## Haproxy Dockerfile


Run haproxy in docker to serve wwebsites from other docker container

Thanks to [Barker's Bits and Bytes](http://blog.dbdevs.com/2014/12/docker-adding-haproxy-and-fig-to-my.html)

As we are running the haproxy container using --link to the other containers, we do not need to know their ip addresses nor expose their ports. Docker will take care of that


### Usage

     docker run -d -p 80:80 -v ~/haproxy-config:/haproxy-override --name haproxy --link nginx:nginx dockerfile/haproxy
     
     Assuming nginx is the name of the container serving the website.

~/haproxy-config should contain

  - `haproxy.cfg`: custom config file
  - `errors/`: custom error responses

Sample haproxy.cfg is provided
