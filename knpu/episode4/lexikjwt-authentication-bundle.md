# Lexikjwt Authentication Bundle

Google for Lexikjwt authentication bundle. This one is going to make creating JSON web tokens really easy. So let’s install it. Click to read the documentation and then you guys know the drill. I’ll grab the composer require line and run composer require Lexikjwt authentication bundle and while we’re waiting on that, we’ll grab the new bundle line and put that into our app current. Great. Ultimately, the main thing that we need to do with JWT is we need to be able to create one of these tokens. 

We will start with a package of information like the user name of the user and then we need something to cryptographically turn that into this special JSON web token structure. There are a number of libraries in PHP that do this and this bundle leverages one of those and gives us a really handy service to do this. Now, in order to create a JSON web token, you need to have a secret key and this is the secret key that allows you to sign those JSON web tokens. So it’s very important that you keep your secret key secret. 

If somebody else gets it, they’ll be able to create new JSON web tokens which you definitely do not want. So we’ll copy these three lines down here at the bottom to create our new public and private keys, but I’m going to change them slightly because we’re on symphony three to put things into the VAR directory. Let’s wait for composer to finish its job. Come on Jordy. Right. And don’t worry about that error. That’s the bundle requiring us to have some configuration which we’ll add in a second. Start with make dir var slash JWT. That will be a new directory that we’ll store our tokens in. 

Second, grab the second line to create a new private key and remove the app so it goes directly into the VAR directory. This will ask you for a password which you should use. It’s another layer of authentication in case somebody gets your private key. Let’s use happy API. Perfect. And then finally grab the last line and this generates the public key off of the private key. If you’re not very comfortable with public and private keys, the point is that we’re creating a cryptographic secret, a secret string that we want nobody else to know and I’ll remove the app from that command. It asks me for the pass phrase. 

Use happy API and there we go. This gives us a public dot PEM and a private dot PEM. Now you probably will not want to commit these to your repository. The main important thing is that they remain secret. Now, they can be different on your local machine than on production. So you can have your own set of public and private key locally that is not so secret and then keep a different one on your production server that is very, very secret and make sure you don’t change it on your production server ever because that will invalidate any existing JSON web tokens that your clients have. 

All right. Last step is to configure the bundle. So I’ll copy the configuration. Open up all config, config dot YML and then go ahead and paste this on the bottom and I’m not going to use quite as many parameters as the author is using. We’ll use kernel dot route there slash dot dot slash var slash JWT slash private dot PM and then we’ll copy that and change it to public dot PM for the next and we copied the JW key pass phrase, but then change the token TTL to 3600 or whatever you want. So this would be – every token has a lifetime so this will make it last for six hours. 

Now I’ll open parameters dot YML and add the date JWT key passphrase set ours to happy API. Then don’t forget to add that to your parameters dot YML dot disk file for future developers. Cool and that’s it. We are ready to go with generating our JSON web tokens. This bundle gave us one important thing and you can see it if you go to debug container and search for JWT. We now have a really handy service for encoding JSON web tokens. 