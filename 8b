import 'package:flutter/material.dart';

void main() {
  runApp(const AnimationDemoApp());
}

class AnimationDemoApp extends StatelessWidget {
  const AnimationDemoApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: AnimationTypesDemo(),
    );
  }
}

class AnimationTypesDemo extends StatefulWidget {
  const AnimationTypesDemo({super.key});

  @override
  State<AnimationTypesDemo> createState() => _AnimationTypesDemoState();
}

class _AnimationTypesDemoState extends State<AnimationTypesDemo>
    with SingleTickerProviderStateMixin {
  late final AnimationController _controller;

  late final Animation<double> _fadeAnimation;
  late final Animation<Offset> _slideAnimation;
  late final Animation<double> _scaleAnimation;
  late final Animation<double> _rotationAnimation;
  late final Animation<double> _sizeAnimation;

  @override
  void initState() {
    super.initState();

    _controller = AnimationController(
      duration: const Duration(seconds: 2),
      vsync: this,
    );

    // Fade Animation
    _fadeAnimation = Tween<double>(
      begin: 0.0,
      end: 1.0,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeIn,
      ),
    );

    // Slide Animation
    _slideAnimation = Tween<Offset>(
      begin: const Offset(-1.0, 0.0),
      end: Offset.zero,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );

    // Scale Animation
    _scaleAnimation = Tween<double>(
      begin: 0.5,
      end: 1.0,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.decelerate,
      ),
    );

    // Rotation Animation
    // 0.0 to 1.0 = one complete rotation
    _rotationAnimation = Tween<double>(
      begin: 0.0,
      end: 1.0,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.linear,
      ),
    );

    // Size Animation
    _sizeAnimation = Tween<double>(
      begin: 100.0,
      end: 200.0,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.fastOutSlowIn,
      ),
    );
  }

  void _toggleAnimation() {
    if (_controller.status == AnimationStatus.completed) {
      _controller.reverse();
    } else {
      _controller.forward();
    }
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Different Types of Animations'),
        backgroundColor: Colors.teal,
        foregroundColor: Colors.white,
      ),

      body: Center(
        child: SingleChildScrollView(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              // Fade Animation
              FadeTransition(
                opacity: _fadeAnimation,
                child: const Text(
                  'Fade Animation',
                  style: TextStyle(
                    fontSize: 18,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),

              const SizedBox(height: 25),

              // Slide Animation
              SlideTransition(
                position: _slideAnimation,
                child: const Text(
                  'Slide Animation',
                  style: TextStyle(
                    fontSize: 18,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),

              const SizedBox(height: 25),

              // Scale Animation
              ScaleTransition(
                scale: _scaleAnimation,
                child: const Text(
                  'Scale Animation',
                  style: TextStyle(
                    fontSize: 18,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),

              const SizedBox(height: 25),

              // Rotation Animation
              RotationTransition(
                turns: _rotationAnimation,
                child: const Icon(
                  Icons.refresh,
                  size: 50,
                  color: Colors.deepPurple,
                ),
              ),

              const SizedBox(height: 25),

              // Size Animation
              AnimatedBuilder(
                animation: _sizeAnimation,
                builder: (context, child) {
                  return Container(
                    width: 200,
                    height: _sizeAnimation.value,
                    color: Colors.amber,
                    alignment: Alignment.center,
                    child: const Text(
                      'Size Animation',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                      ),
                    ),
                  );
                },
              ),
            ],
          ),
        ),
      ),

      floatingActionButton: FloatingActionButton(
        onPressed: _toggleAnimation,
        child: const Icon(Icons.play_arrow),
      ),
    );
  }
}



